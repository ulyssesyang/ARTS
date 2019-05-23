# Share: Understanding Basic Elements of Distributed Architecture

Architecture is opinion. However, there are 6 basic common elements to be used to build the architecture.

## 6 Elements of Distributed Architecture

### Information

Information is what it's all about.
Two big categories:

* Events: Information you find out about
* Storage: Information you're aware of

Very many different detail characteristics

### Communication

Transfer information from somewhere to somewhere else
Two big categories:

* Synchronous communication: both parties are connected, listening to monologs or having dialogs
* Asynchronous communication: parties are not connected and communicate via intermediaries

### Presentation

Present information at the edge of a system for consumption or manipulation
Two big categories:

* Read-only information dissemination/consumption
* Read/write information presentation/manipulation

### Processing

Process information to yield post-processing information output or other desired side effects
Two big categories:

* Processing jobs that run on Silicon time (server machine control)
* Processing jobs that run on Human time (Human control)

### Failure Management

Failure Management is about explicitly dealing with things (Communication, Information Storage, Processing) going wrong
Two big categories:

* On failure, make everything look like nothing happened at all (Isolate)
* On failure, compensate for whatever went wrong (Compensate)

### Protection

Protection is about securing and safeguarding information from undesired access, modification, or destruction
Two big categories:

* Security guards against unauthorized actions (Security)
* Safety guards against unintended actions or hard failures (Safety)

## Adversaries during building architecture: Software's Forces of Nature

### Capacity

### Latency

### Affinity

The degree to which a particular set of information is bound to a scope or location and is the biggest inhibitor for scaling out:

* Affinity of original and intermediate state to a particular sequence of processing while producing a desired output
* Affinity of information to a particular container due to size or transfer latency
* Affinity of transfer to a particular communication route
* Affinity to a particular physical device or location (including someone's pocket)

### Intermittent Failure

Any condition that interrupts or otherwise adversely affects the common, planned flow of information processing

* Programming errors
* Physical failure of equipment
* Exhaustion of system capacity
* Environment conditions

### Thieves and Idiots

* Security protects against thieves:
    Identity who you're dealing with (authentication)
    Only allow them to do what they're entitled to do (authorization)
* Safety protects against idiots (Safety)
* Security and safety are about undesired interactions with people