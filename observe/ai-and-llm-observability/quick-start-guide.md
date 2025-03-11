# Quick Start Guide

## Ascent Quick Start Guide for AI and LLM Observability

The Apica full-stack observability platform combined with the OpenTelemetry SDK can seamlessly provide comprehensive insights into Large Language Models (LLMs) in production environments. By observing AI models, businesses can make informed decisions, optimize performance, and ensure compliance with emerging AI regulations.

This guide will walk you through setting up OpenTelemetry Auto Instrumentation for traces and metrics to fully monitor your LLM application using Apica Ascent. Once the quick setup is complete, you can easily track and analyze the performance and usage of your LLM applications.

Here are the main configuration steps required within your application code:

### **Deploy OpenTelemetry SDK**

Follow the steps below for either traces or metrics (or both). Also, we provide the links to the OTEL deployment guides if needed.

a.         OTEL tracing setup guide: [https://opentelemetry.io/docs/concepts/signals/traces/](https://opentelemetry.io/docs/concepts/signals/traces/)

b.         OTEL metrics setup guide: [https://opentelemetry.io/docs/specs/otel/metrics/](https://opentelemetry.io/docs/specs/otel/metrics/)

### **Instrument your Application**

Configure OTEL to send traces and/or metrics into Ascent (depending on how you want to visualize the data). Below are example(s) of code required to enable instrumentation of OTEL – traces.

#### TRACING code examples:

Imports (FastAPI might differ depending on what framework your app is created with):

```bash
from opentelemetry.sdk.resources import Resource
from opentelemetry import trace
from opentelemetry.instrumentation.fast.api import FastAPIInstrumentor
from opentelemetry.instrumentation.asyncio import AsyncioInstrumentor
from opentelemetry.sdk.trace import TraceProvider
from opentelemetry.sdk.trace.export import BatchSpanProcessor
from opentelemetry.exporter.otlp.proto.grpc.trace_exporter import OTLPSpanExporter
```

Tracing configuration:

```bash
#tracing configuration
resource = Resource.create(attributes={"service.name": "llm-app-service"})

trace.set_tracer_provider(TracerProvider(resource=resource))
tracer = trace.get_tracer_provider().get_tracer(_name_)

otlp_exporter = OTLPSpanExporter(endpoint="http://localhost:4317", insecure=True)
trace.get_tracer_provider().add_span_processor(BatchSpanProcessor(otlp_exporter))
```

Instrument App (Otel supports more than just FastAPI, simply import correct API in step #1):

```bash
# Apply OpenTelemetry instrumentation to FastAPI
FastAPIIstrumentor.instrument_app(app)
```

Add tracer to each API call you would like to track. In this example we are adding a trace on “create\_chat\_completion” with a span called “chat\_completion”:

```python
async def create_chat_completion(request: Request, body: CreateChatCompletionRequest):
    with tracer.start_as_current_span("chat_completion") as span:
```

To add custom attributes such as prompt tokens to the trace:

```python
#tracing
span.set.attribute("prompt.tokens", str(response["usage"].get("prompt_tokens", 0)))
```

METRICS code examples:



Imports:



Metric Configuration:



Creating a metric:\




Assigning the metric a value:\




In this example we are grabbing prompt\_tokens from the LLM response and assigning it to the “prompt\_tokens\_counter” metric. We also added some metadata to the metric by adding “model\_name”.



**3.         Collect and store data:** Data is stored in Ascent Lake

**4.         Visualize data:** View individual traces and metrics within Ascent Explore. Use data explorer to visualize data – creating a widget for each desired “metric” to visualize within a dashboard – follow dashboard configuration steps:

a.         Metric data – follow the data explorer for metrics

b.         Trace data – use log2metric to visualize traces

**5.         Alerting:** Configure alerts as required within Ascent.
