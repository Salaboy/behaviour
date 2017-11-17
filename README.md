# Behavioural contracts
The following document is just a brain dump of how to isolate behaviour from low level implementation details. This ideas tries to define some high level concepts to bundle behaviour that is self contained and can be (automated) executed in an autonomous way. 

Following the practices of BPM, decision management, case management, using rule engines and Complex Event Processing, they all follow the same lifecycle which has clear limits between the authoring phase and the execution phase. With the rise of microservices, continuous deployments these lines (usually barriers) need to go down. We are finally getting close to shop software quite fast, that means that From modelling to runtime needs to be fast, we cannot slow down other initiatives. 

All these business models (processes, rules, cases, decisions) depends on a domain model to work, so there must be a clear interface between our domain models and our business models. Domain models require validations when they are used or referenced in our business models. 

We need a high level domain model description. JSon and json schemas sounds like the right tool for the job, but we need to make sure that we can manipulate these domain models at different levels of abstractions. Users might want to write behaviour using these model, and we should be able to execute these behaviour at some point.

## Execution 
Executing behaviour requires us to consider the following expectations:
* Behaviour requires data to be executed 
* This data needs to be retrieved/stored somewhere (and we might need to deal with part or of the data storage and data duplication)
* Behaviour needs to be rigorously tested before it can be executed
* From the end user point of view, the modeles behaviour needs to be fully understood and there must be no surprises at execution time
* End users doesn’t care where the behaviour is executed, and they will expect to have different version of the same behavior being executed at the same time for different scenarios. 
* The list of running behaviors is dynamic and up to the business users
* The list of behaviors that can be started is also dynamic and context aware

Based on these expectations the following sections tries to provide a high level definition for Behavior Definitions, the execution semantic and deployment mechanisms associated with these practices.

# Behavior Definition Language
For some clarity, we will need to have different types of underlaying behavior categories which are mostly implicit for the end users, but they will drive our low level choices for execution:
- Procedural: for certain situations follow these steps
- Deductive / Inductive: If this then that  
- Reactive: look for these data (filters) and let me know when something matches: When this then that. This might include temporal correlations

Notice that a cross cutting concern for all these categories of behaviors is tracebility/justification capabilities. No matter the category you choose, after executing your behavior you will have a trace of what happened and why (mix of the behavior definition + data that was used to execute it). 

All of these types of behavior require the use of Domain specific Data which needs to be provided for the behavior to be executed and for this reason we need the data (structures) first before we even start thinking about writing behaviors. Once we have the data we need to provide a user centric language (or a preferred option will be a tool) to model these behaviors which will act on our Domain Models. 

This tool or language, will have the Domain Objects and first class citizens, and we need to make sure that our Domain Objects are not polluted with technical details to not clutter the tool with non-sense for our users. 

Let’s imagine how the tool should look like in order to articulate better how what are the language capabilities. 







