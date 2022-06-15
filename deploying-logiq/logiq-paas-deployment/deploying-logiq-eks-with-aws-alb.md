# Deploying Logiq EKS with AWS ALB

Application Load Balancer inspects packets and creates access points to [HTTP](https://whatis.techtarget.com/definition/HTTP-Hypertext-Transfer-Protocol) and [HTTPS](https://searchsoftwarequality.techtarget.com/definition/HTTPS) headers. It identifies the type of load and spreads it out to the target with higher efficiency based on application traffic flowing in HTTP messages. Application Load Balancer also conducts health checks on connected services on a per-port basis to evaluate a range of possible code and HTTP errors. A developer receives detailed metrics following the checks.

Prerequisites:

* Verify that coffee running as a NodePort service.

```
k get svc -n test coffee

NAME     TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
coffee   NodePort   10.100.11.193   <none>        80:32165/TCP   40h
```

* Download the below code into a file and create a flash-ml nodeport service as shown below by applying the file using kubectl.

```
kubectl apply -f flash-ml-nodeport.yaml
```

```
apiVersion: v1
kind: Service
metadata:
  annotations:
    meta.helm.sh/release-name: <release-name>
    meta.helm.sh/release-namespace: <namespace-name>
  labels:
    app: logiq-flash-ml
    app.kubernetes.io/managed-by: Helm
    chart: logiq-flash-1.0.0
    heritage: Helm
    promMonitor: logiq-flash
    release: test
  name: logiq-flash-ml-np
  namespace: test
spec:
  ports:
  - name: grpc
    port: 8081
    protocol: TCP
    targetPort: 50054
  - name: webcli
    port: 9998
    protocol: TCP
    targetPort: 9998
  - name: api
    port: 9999
    protocol: TCP
    targetPort: 9999
  - name: liveness-port
    port: 8080
    protocol: TCP
    targetPort: 8080
  selector:
    app: logiq-flash-ml
    release: test
  sessionAffinity: None
  type: NodePort 
```

### ALB integration:

Create 3 Target groups.

* Target group coffee

![](https://lh4.googleusercontent.com/8Pw1H9jtBYbaTfNo\_s0g9W0G3\_CzxGpCacAR2wDhIZcV4oTcBWo59\_95KYldYK6D5Q86r4xKJsQ1yvumbOo9YpqU\_DD5REH6hJ9pClYVMgQyQURGHxQubHv7z0n3abQeTfcwRE-x)

* Create 2nd target group for Flash

![](https://lh6.googleusercontent.com/Z9Zp9kTwUgZJl8ffrLM5rAq414sRY\_tPv40pLU\_zJfnYPkDAljR89cROfsSzeX8pMXdUc36JVVR\_o5DyLOVyj-yMv3UdJy\_C9-cT9pQDm8uLuLBjGj55OP8LwzxL4BSMlI\_uG7Yn)

Create target group for flash-ml, pick the nodeports from flash-ml-np service

```
kubectl get svc -n test|grep flash-ml 
logiq-flash-ml-np NodePort 10.100.123.89 8081:32232/TCP,9998:31194/TCP,9999:31126/TCP,8080:31001/TCP
```

&#x20;Replace port with nodeport mapped to 9999 and health port (additional settings) mapped to 8080 as shown below.

![](https://lh3.googleusercontent.com/ai7ig51CnmjxOPITELhvZ0ufkRpGPjSfHVj8MhNgjYnjInqwI7yfJyAg\_rGc2xbdrBuXmjkHDviLg-Sxh6I34fGyNTBTcvSxDt1xV79HUi1HaaoFQczV9z9euwUC7nIUAYHE8wxr)

Logiq would have created auto scaling group for common and Ingest nodes. Associate the Ingest ASG with flash target group.

![](https://lh3.googleusercontent.com/X4o\_29hFbuPqDFSPMxShLmRgfqYhzN5EbTWWT4za\_snOG3JJ9JEEmsiGMLDjStRh83qeleN8ZREv9z5HCIWGxdxAiGMTYXYKQ0tzAxNUbN0FGacLj6HFIokuIJ4jshL0mJTMoRPu)

Associate the common ASG with 2 groups created

![](https://lh6.googleusercontent.com/y8ERNyhZUBPRwvQfOBRRdFgj1GWCCGonLi0SUAcEKGaQ974yuZ2iICz4YJG-PKLOWBPg25laey4Id44fFNlv7VmYbXKf9ifmBSE4Wtk66qlzg6S54Bus6xWVP3nyqvqrtCFkJwm\_)

Create Application load balancer and in the listener section

![](https://lh3.googleusercontent.com/eulpuoynsPsJ3EfyDbGPdC0DTBWCI9IgclDknOzaLxMyIorwVkgLzp7YigT3WypHj5fr5dPT\_ZVBURxsbCACe33KcNUuNNTP6EpgQkX4fRflxe1dNsWadsg8WDOeRr0nlzZ5zzKw)

We need to route the traffic as per the below below ingress rules along with the service.

```
   rules:
    - http:
        paths:
        - backend:
            service:
              name: coffee
              port:
                number: 80
          path: /*
          pathType: ImplementationSpecific
        - backend:
            service:
              name: logiq-flash
              port:
                number: 9999
          path: /v1/json_batch
          pathType: ImplementationSpecific
        - backend:
            service:
              name: logiq-flash
              port:
                number: 9999
          path: /v1/json
          pathType: ImplementationSpecific
        - backend:
            service:
              name: logiq-flash-ml-np
              port:
                number: 9999
          path: /v1/*
          pathType: ImplementationSpecific
        - backend:
            service:
              name: logiq-flash-ml-np
              port:
                number: 9999
          path: /v2/*
          pathType: ImplementationSpecific
        - backend:
            service:
              name: coffee
              port:
                number: 80
          path: /*
          pathType: ImplementationSpecific

```



Click on manual View/edit Add edit rules, click on + section and configure the rules as shown below to the various target groups.

{% hint style="info" %}
Note: The rules should be in the same order as shown below
{% endhint %}

![](https://lh4.googleusercontent.com/X7Ih0K85bHasXm8uvJRA223ZUBQgIKrDTCoR-dstI48FT0qtJWtjL\_2LcC1CKbcqkTC15LTwsyPNYTBUVb8yyIU8RKHtdIhFRsreTzlROrXCLzPZt6kcE1-ZDAkPSXi9UpqCdN8o)

If you have deployed the Logiq on private subnet, you may need to map global accelerator (under Integrated services) to access the public endpoints and DNS on top of it.&#x20;

![](<../../.gitbook/assets/image (20) (1).png>)

If you want to route traffic on http(port:80), ensure your listener rules are configured on port 80

![](<../../.gitbook/assets/image (16).png>)

If you want to route traffic on https(port:443), ensure your listener rules are configured on port 443. As a prerequisite, your global accelerator should have all the certificates configured for this to work.

![](<../../.gitbook/assets/image (12).png>)
