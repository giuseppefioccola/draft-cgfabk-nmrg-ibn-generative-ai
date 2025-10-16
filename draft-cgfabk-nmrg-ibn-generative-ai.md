---
title: "Generative AI for Intent-Based Networking"
abbrev: "ibn-generative-ai"
category: info

docname: draft-cgfabk-nmrg-ibn-generative-ai-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "IRTF"
workgroup: "Network Management"
keyword:
 - next generation
 - unicorn
 - sparkling distributed ledger
venue:
  group: "Network Management"
  type: "Research Group"
  mail: "nmrg@irtf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/nmrg"
  github: "giuseppefioccola/draft-cgfabk-nmrg-ibn-generative-ai"
  latest: "https://giuseppefioccola.github.io/draft-cgfabk-nmrg-ibn-generative-ai/draft-cgfabk-nmrg-ibn-generative-ai.html"

author:
 -
    fullname: Pietro Cassara'
    organization: CNR-ISTI
    city: Pisa
    country: Italy
    email: pietro.cassara@isti.cnr.it
 -
    fullname: Alberto Gotta
    organization: CNR-ISTI
    city: Pisa
    country: Italy
    email: alberto.gotta@isti.cnr.it
 -
    fullname: Giuseppe Fioccola
    organization: Huawei Technologies
    city: Vimodrone (Milan)
    country: Italy
    email: giuseppe.fioccola@huawei.com
 -
    fullname: Aldo Artigiani
    organization: Huawei Technologies
    city: Turin
    country: Italy
    email: aldo.artigiani@huawei.com
 -
    fullname: Riccardo Burrai
    organization: SIRIUS Technology
    city: Prato
    country: Italy
    email: riccardo.burrai@siriustec.it
 -
    fullname: Emiljan Kolaj
    organization: SIRIUS Technology
    city: Prato
    country: Italy
    email: emiljan.kolaj@siriustec.it
 -
    fullname: Marco Martalo'
    organization: University of Cagliari
    city: Cagliari
    country: Italy
    email: marco.martalo@unica.it
 -
    fullname: Virginia Pilloni
    organization: University of Cagliari
    city: Cagliari
    country: Italy
    email: virginia.pilloni@unica.it

contributor:


normative:

informative:
  AI-Challenges: I-D.irtf-nmrg-ai-challenges
  IBN-UseCases: I-D.irtf-nmrg-ibn-usecases
  LoRA: DOI.10.48550/arXiv.2106.09685
  HF-PEFT:
     target: https://github.com/huggingface/peft
     title: Hugging Face PEFT

--- abstract

This document describes how to specialize AI models in order to offer a scalable, efficient path to creating
highly targeted generative models for Intent-Based Networking.


--- middle

# Introduction

This document describes how transfer learning techniques can be adopted to design generative AI specialized models
for Intent-Based Networking (IBN). It also describes tools, such as Low-rank Adaptation (LoRA), for achieving
efficient and scalable transfer learning in data networks for designing targeted generative models for
Intent-Based Networking (IBN).

The objective of this document is define a framework for the rapid adaptation and composition of specialized knowledge,
addressing the challenges identified in {{AI-Challenges}} and enabling the dynamic, multi-domain use cases of {{IBN-UseCases}}.

Future work should focus on interoperability, governance, and autonomous management to fully realize the potential of this approach.

## Overview of IBN

IBN represents a paradigm shift in network management, aiming to bridge the gap between business objectives and network configurations.
Unlike traditional networking, which requires manual, device-level configurations, IBN allows operators to specify high-level intents
(e.g., "ensure low latency for video traffic"), which the system then automatically translates, enforces, and continuously validates.
Key references include {{IBN-UseCases}}, which outlines IBN use cases across enterprise, data center, and service provider environments.

IBN fundamentally changes the role of network administrators by focusing on desired outcomes instead of manual command-line configurations.
The system must be capable of not only translating intents into actionable policies but also of continuously validating whether those intents are met.
This requires advanced mechanisms for policy enforcement, telemetry collection, and feedback loops that ensure alignment between
high-level business goals and actual network performance.
IBN can reduce operational complexity, improve network agility, and significantly lower the time required to deploy new services.

## Role of Generative AI in IBN

Generative AI, particularly Large Language Models (LLMs), can enhance IBN by automating intent parsing, policy generation, and network troubleshooting.
LLMs can understand natural language intents, generate low-level configurations, and adapt policies in real-time.
This aligns with the challenges presented in {{AI-Challenges}}, which stresses the need for models that can dynamically adapt to context and scale efficiently.

Generative AI can extend its role to include auto-remediation, dynamic configuration adjustments, and the creation of context-aware policies
based on real-time network conditions. These capabilities are critical in environments with rapidly shifting traffic patterns,
such as 5G networks, multi-cloud environments, and large-scale SDN deployments.
By leveraging fine-tuned generative models, IBN systems can become self-configuring, self-optimizing, and self-healing,
moving closer to the vision of fully autonomous networks.

## Motivation for AI Model Specialization

Generic LLMs often lack the precision required for domain-specific applications like IBN. Specialization is critical to
improve accuracy, reduce inference time, and minimize resource consumption.
LoRA provides an efficient method to fine-tune large models using minimal computational resources, enabling targeted model specialization
for distinct network domains or intent categories.

Specialization ensures that the AI system correctly interprets and applies complex domain-specific policies, such as those for
Quality of Service (QoS), security compliance, and multi-vendor interoperability.
Without specialization, generic models risk generating suboptimal or even invalid configurations.
LoRA-based specialization enables the rapid creation and deployment of these focused models, supporting agile, intent-driven network operations
while maintaining the scalability and cost-effectiveness required for wide deployment across heterogeneous infrastructures.

## Transfer Learning

Transfer learning enables pretrained models to adapt to specific tasks with significantly less data and computational resources.
In the context of IBN, this approach offers a dual advantage: enhancing the efficiency of model training and improving the reliability of
intent recognition and execution. Indeed, it avoids the need for building models from scratch, which is not only resource-intensive
but also prone to overfitting due to limited labeled network-specific data. By fine-tuning models on domain-specific datasets, developers
can quickly create robust models that interpret network intents with high accuracy. Furthermore, it facilitates cross-domain knowledge integration,
allowing the model to generalize better across various networking environments and topologies.
Additionally, continual learning mechanisms can be integrated into the LLM-based IBN framework to refine performance over time,
incorporating feedback loops that learn from real-world interactions and user corrections.

In conclusion, transfer learning significantly boosts the viability of LLM-based solutions in IBN by offering a cost-effective,
accurate, and scalable method for intent interpretation and execution.
This fusion of LLMs with transfer learning not only propels the automation of network operations but also ensures that the AI systems remain adaptive,
interpretable, and aligned with organizational objectives in dynamic digital infrastructures.

# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Background Concepts

## Generative AI and LLMs in Networking

LLMs like GPT and BERT can process complex, unstructured inputs and generate contextually relevant outputs.
In IBN, LLMs are used to translate high-level intents into vendor-agnostic policies and device-specific configurations.
The integration of these models into network management systems is emerging as a critical research area,
as outlined in {{AI-Challenges}}.

## Intent Parsing and Translation via Generative Models

An example flow in {{fig1}} illustrates how an intent like "minimize latency for video traffic" is parsed
by a generative model and translated into specific QoS policies.

~~~
+---------------------+
|  User High-Level    |
|       Intent        |
+---------------------+
           |
           v
+---------------------+
|  Generative Model   |
| (Intent Parser +    |
|  Policy Generator)  |
+---------------------+
           |
           v
+-----------------------+
| Network Configuration |
+-----------------------+
~~~
{: #fig1 title="Example flow of intent parsing and translation"}

## Fundamentals of LoRA

LoRA {{LoRA}} introduces trainable low-rank matrices into the layers of pre-trained models, allowing fine-tuning
with significantly fewer parameters. This approach reduces the storage and computational footprint,
enabling deployment of specialized models even on resource-constrained systems.


# Specializing Generative AI with LoRA

## The Need for Model Specialization in IBN

IBN requires high domain accuracy. For example, a generic model may misinterpret a telecommunications-specific intent.
Specializing models using LoRA ensures they are finely tuned to the nuances of networking language, policies, and protocols.

## LoRA for Lightweight Fine-Tuning

LoRA fine-tunes only small, low-rank matrices, leaving the rest of the model unchanged.
For instance, adapting a generic LLM to focus on BGP policy generation could be achieved
by training a small adapter on BGP-related datasets, reducing the compute requirements compared to full fine-tuning.

## Comparison with Traditional Fine-Tuning and Pruning

Unlike traditional fine-tuning, which adjusts the entire model, or pruning, which removes less important weights,
LoRA introduces new parameters without overwriting existing knowledge. This allows multiple specialized LoRA adapters
to coexist and be swapped or combined as needed.

## Efficiency and Performance Gains in Network Models

Empirical studies show that LoRA adapters can reduce memory consumption by over 70% compared to full fine-tuning.
For example, fine-tuning a model for IPv6 routing policy generation using LoRA reduces the required GPU VRAM
from 16 GB to approximately 5 GB while maintaining performance.


# Hub: Repository of Specialized Models

## Concept and Architecture of a Hub

A Hub is a structured repository where specialized adapters are stored, indexed, and shared.
It enables efficient reuse and modularity. The architecture typically includes:

- Adapter storage
- Metadata index (domain, use case, version)
- Dependency tracking for composite models

## Organizing and Indexing Adapters for Networking Tasks

Adapters can be categorized by networking domain (e.g., security, QoS, routing) and intent granularity (e.g., traffic type, SLA constraint).
Cross-indexing improves discoverability and composability.

## Examples of IBN-Targeted LoRA Adapters

- Adapter A: IPv6 Segment Routing configuration
- Adapter B: QoS policy for video prioritization
- Adapter C: Security baseline for zero-trust architectures

## Benefits of Modular and Shareable Specializations

Operators can quickly compose or replace adapters based on current intents, improving agility and reducing the cost of specialization.
LoRA Hub supports collaboration and community-driven model evolution.


# Flow: Model Fusion and Evolution

## Concept of Flow for Adapter Composition

Flow refers to the systematic combination of multiple adapters to form a new, composite model capable of handling complex, multi-domain intents.

## Fusion of Multiple Adapters to Generate New Models

Example: Combining an adapter for SLA enforcement with another for security compliance to address intents
like "guarantee low latency for critical applications within zero-trust boundaries."

~~~
     +-------------------------+
     |        Base LLM         |
     +-------------------------+
       |        |    ...   \
       |        |           \
+---------+ +----------+   +----------+
| Adapter | | Adapter  |   | Adapter  |
|   QoS   | | Security |...|     j    |
+---------+ +----------+   +----------+
        \        |            /
         \       |    ...    /
         +-------------------+
         |     Composite     |
         |    Specialized    |
         |       Model       |
         +-------------------+
~~~
{: #fig2 title="Fusion of multiple adapters to generate new models"}

## Workflow for Dynamic Specialization Based on Intent

1. Parse user intent
2. Query LoRA Hub for relevant adapters
3. Dynamically load and fuse adapters
4. Generate configuration

## Case Study: Multi-Domain Network Management

A service provider managing both MPLS and SDN domains can fuse LoRA adapters for each to generate cross-domain policies
automatically in response to high-level intents.


# Lifecycle of Specialized Models in IBN

## Model Generation, Evaluation, and Deployment

- Generation: Fine-tuning on domain datasets
- Evaluation: Accuracy, latency, resource profiling
- Deployment: Containerized adapters for on-demand loading

## Feedback Loops and Continuous Adaptation

In-network telemetry provides real-time feedback on policy effectiveness, enabling further fine-tuning or adapter updates,
aligning with the adaptive model requirements discussed in {{AI-Challenges}}.

## Benchmarking Specialized Models: Accuracy, Latency, and Resource Consumption

Key benchmarks include:

- Policy generation latency (< 50 ms target)
- Memory footprint reduction (70% over full models)
- Domain-specific intent accuracy (> 90%)


# Practical Frameworks and Tools

## LoRA Fine-Tuning Libraries

- PEFT (Parameter-Efficient Fine-Tuning) {{HF-PEFT}}
- Hugging Face LoRA integration

## LoRA Hub Implementations

- Model repositories using Hugging Face Hub structure
- Metadata indexing via JSON-LD for semantic search

## Toolchains for LoRA Flow and Adapter Fusion

- Adapter composition APIs
- Intent parsing frontends
- Deployment via Kubernetes with sidecar loading of adapters


# Logical Architecture for Model Management

## Overview

Drawing inspiration from the Analytics Logical Function (AnLF) and Model Training Logical Function (MTLF) architectures defined in 3GPP NWDAF,
this section proposes a logical architecture to manage, store, and orchestrate AI models for Intent-Based Networking.
The architecture introduces the following logical components:

- Model Repository Function (MRF): Stores adapters and base models.
- Model Training and Specialization Function (MTSF): Handles fine-tuning, evaluation, and versioning.
- Model Fusion and Composition Function (MFCF): Manages flow processes to create composite models.
- Intent Processing and Adapter Orchestration Function (IPOF): Dynamically selects, composes, and deploys adapters based on parsed intents.
- Telemetry Feedback Function (TFF): Continuously monitors performance and triggers model re-specialization when required.

## Logical Architecture Diagram

~~~
+----------------------------+
|      Intent Interface      |
+----------------------------+
              |
              v
+-------------------------------+
|    Intent Processing and      |
|  Adapter Orchestration (IPOF) |
+-------------------------------+
              |
              v
+------------------------------+
| Model Fusion and Composition |
|         (MFCF)               |
+------------------------------+
              |
              v
+-----------------------------+
|  Model Repository (MRF)     |
+-----------------------------+
              ^
              |
+---------------------------------+
| Model Training & Specialization |
|          (MTSF)                 |
+---------------------------------+
              ^
              |
+-----------------------------------+
| Telemetry Feedback Function (TFF) |
+-----------------------------------+
~~~
{: #fig3 title="Logical Architecture Diagram"}

## Detailed Workflow

1. Intent Reception: User or application submits a high-level intent through the Intent Interface.
2. Adapter Orchestration: IPOF parses the intent, queries the MRF for relevant adapters, and orchestrates dynamic fusion via MFCF.
3. Model Fusion: MFCF composes adapters into a composite model tailored to the intent.
4. Deployment: The composite model is deployed into the IBN system to generate specific configurations.
5. Telemetry Feedback: The TFF monitors the applied configurations' impact on network KPIs and feeds insights back to IPOF and MTSF.
6. Re-Specialization: If performance deviates from expected thresholds, MTSF initiates LoRA re-training or fine-tuning using new data collected via TFF.

## Models Adaptation, and Orchestration

This architecture closely follows the modularity principles of NWDAF's AnLF for real-time analytics and MTLF for model training and distribution,
enabling scalability, continuous learning, and rapid specialization across distributed edge and core network nodes.
Each function can be independently scaled and containerized, ensuring fault tolerance and efficient resource utilization.
This logical separation allows efficient model lifecycle management, supports federated learning, and can integrate
with standard IBN orchestrators via REST APIs or 3GPP-compatible interfaces.


# Network Digital Twin Ontology

The proposed generative AI–enabled Intent-Based Networking (IBN) architecture can be empowered with a Network Digital Twin (NDT) ontology,
which serves as the semantic backbone that allows the system to represent, reason, and act upon the network’s physical and logical states in a unified way.
Since the adapters are categorized by networking domain and intent granularity with different quality parameters, the ontology has to be quality-driven,
meaning that its core entities and relationships are structured around quality indicators such as latency, throughput, reliability, and energy efficiency.
The ontology relies on a semantic representation so that every network element (node, link, function) is described by its functional attributes
together with quantifiable quality parameters. This enables intelligent alignment between service requirements and underlying resource capabilities through IBN.
Within the overall generative AI-enabled IBN model, the ontology provides a multi-layered abstraction that connects service requirements with traffic parameters
and physical infrastructure, supporting both top-down intent translation and bottom-up feedback from telemetry data. This ontology enhances the adapter fusion and
orchestration processes by guiding AI models to interpret intents in the context of network quality objectives, select appropriate policy actions, and evaluate
trade-offs between performance and efficiency. By embedding these semantic and quality-aware relationships, the NDT ontology enables the digital twin
to operate as a continuously learning system, capable of dynamically optimizing network behavior, validating intents before deployment, and adapting to evolving conditions
while maintaining compliance with quality and energy-efficiency goals.


# Challenges and Research Directions

## Model Interoperability in LoRA Flow

Ensuring consistent parameterization and preventing interference when fusing adapters.

## Ensuring Security and Robustness in Specialized Adapters

Preventing malicious adapter injection and ensuring adapters respect security constraints.

## Governance of LoRA Repositories

Managing trust, versioning, and deprecation of adapters.

## Towards Autonomous Model Lifecycle Management in IBN

Developing self-optimizing pipelines for adapter generation, validation, and retirement.


# Security Considerations

TODO


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO
