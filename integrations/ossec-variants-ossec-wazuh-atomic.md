# OSSEC Variants (OSSEC/WAZUH/ATOMIC)

### Overview

LOGIQ.AI supports ingesting security events logs directlry from OSSEC compatible agents. OSSEC (Open Source Security) is a powerful, open-source host-based intrusion detection system (HIDS) developed to detect and prevent malicious activities on systems. It has the ability to monitor all types of environments, including Windows, Mac OS X, Linux and Solaris systems. OSSEC works by monitoring the system.

The OSSEC architecture consists of three main components: the manager, the agent, and the local OSSEC server.

**The manager** is responsible for managing the agents, which monitor system activity and report back to the manager. The manager then compiles the agent reports, combines them with its own rules and tests, and alerts if there are any security issues.

**The agents** watch files, directories and network connections for changes or anomalies in data flow that could signify a malicious attack. Agents can detect attacks from worms, viruses, hacking tools, and more. The agent also looks for any unauthorized changes to critical system files or configurations that could indicate an attempted breach of security.

**The local OSSEC server** is responsible for analyzing the data from the agents and taking appropriate action depending on the type of attack detected. This can involve sending out alerts, blocking traffic, performing forensic analysis, and more.

OSSEC is an incredibly powerful tool that can be used to detect and prevent malicious activities on systems. It is an invaluable asset for any organization looking to secure their networks from threats both outside and within the company.

LOGIQ.AI takes over the functions of the manager and the local OSSEC server and makes it easy to bring together security related events into your data fabric for instant consumption.

### Starting the manager, ossec server

Launching the LOGIQ.AI OSSEC components is accomplished by launching the OSSEC Input _"App Extension"_ which can be found under _"Explore"_

<figure><img src="../.gitbook/assets/Screen Shot 2023-01-02 at 10.19.49 PM.png" alt=""><figcaption><p>Launch the OSSEC HIDS components in LOGIQ.AI</p></figcaption></figure>

You can now provide the credentials that that the agents can use to connect to LOGIQ.AI instance

<figure><img src="../.gitbook/assets/Screen Shot 2023-01-02 at 10.24.04 PM.png" alt=""><figcaption><p>OSSEC Agent auth token</p></figcaption></figure>

### Configuring the agents

OSSEC/Wazuh/Atomic agents can connect to the LOGIQ.AI instance using agent-auth tool

<pre><code><strong>agent-auth -m &#x3C;logiq.ai instance> -p 1514 -P &#x3C;auth token> -A &#x3C;agent identifier>
</strong></code></pre>
