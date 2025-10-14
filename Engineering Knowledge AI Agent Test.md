## 1. Differences between REST API and MCP in the Context of AI

The differences originate from their initial design. The **REST API** approach is generalist, working on any system prior while **MCP’s** ultimate goal is to help LLM-based agents interact with existing systems by standardizing the features that support modern Agentic workflows. Both are relevant to agentic use cases since they operate within the domain of tool-calling features, but MCP’s advantage over its predecessor is that it provides a standardized and efficient way to integrate your tool. You might be able to just define your REST API+JSON schema tool on a tool-calling node and manage it that way, but this would become troublesome when your array of tools expands and your agentic workflow becomes more complex. In addition, the agentic pipeline itself is stateful and you want to manage your tools in such a way that they share context, which would be factored your problem exponentially. Hence, MCP would save you the hassle of managing it.

---

## 2. How REST API and MCP Can Improve AI Use Cases

In essence, both are used to enable clients to interact with resources of targeted machine. Having that liberty, the improvement of AI use case would depend on what kind of service do we have access in but overall direction, in my opinion, would revolved around this use cases:

#### A. Knowledge Enrichment
Just like human, we need to keep up to date to the current fact so we could serve more nuanced and rich answer. Since LLM only know things that they trained on, having ability to read the fact externally would be cheaper option to have timeless and accurate model. 

#### B. Knowledge Grounding
Once again, Just like human, an ability to do fact checking before acting on it would increase the trustworthiness of AI implementation.

#### C. Action Enablement
What is the advantage of human compared llm in term of usefullness? the ability to act on what they think. Those protocol would bridge the gap to allow them to have a capability to act on something that they feel right to solve your issue which ultimately increase its usefullness.

---

## 3. How to Ensure Your AI Agent Answers Correctly
We could ensure its reliability within seperate development phases:
#### 1. Initialization
Before we jump into the development, we need to clarify the scope of the agent. The rule of thumb is to avoid over generalization of task. So, the agentic workflow design need to adhere requirements in away that eliminating possible deviation. Furthermore, we need to identify possible leaked within the design, especially the unavoidable one, and documented it so during the development phase we would aware of this risk.
#### 2. Development
Typical must-implemented node within Agentic pipeline to assure its correctness would be validation and evaluation. Validation wll crosscheck agentic responses/action to possible factual resources while validation is to check structural correctness of its answer heuristically, statistically, even using LLM as judge. Furthermore, since we thoroughly analyze the possible leakage based on our design, we could identify what kind of railguard that suitable to mitigate that (prompting, response structure, or state railguarding).
### 3. Deployment
In this stage, we will have learned lesson from our development effort. Hence we need to understand to ensure our service correctness, we need be able to observe it to identify behaviour deviation before it was too late to take back. Hence, implementing observability features in the hand before going live would be a must-do list.

---

## 4. Describe what can you do with Docker / Containerize environment in the context of AI
It usefullness could be identified using different perspective:
#### A. Researcher
- Docker allow us to have experiment enviroment standarization which is quick and easy setup (no need to engineered stuff, focus on the research).
- Research finding could be packed, and then reproduce its results consistently, increasing your research transparancy
#### B. Developer
- The finickiness of AI application cannot be avoided. One additional character on your prompt or your application seeds might changes parts of your system. Docker safe you from anxiety on scaling your AI application.
- Docker would rapidly help us on creating multiple prototype of POC in one machines. Its likely you need to work on various POC so, having isolated environments to run multiple, potentially resource-hungry applications helps your workflow by preventing them from interfering with each other.
- We would get any inherent perks similar to any system which deployed using docker.

---

## 5. How do you finetune the LLM model from raw ?
Before starting on finetuning, we need to identify whether we have necessary resources to do that (data, conputing power, etc) to do that and if it is make sense to do that. Resource needed might vary depending on use cases so it would be different case by case. Identifying the right use case for doing finetune would also important before starting on grueling and might-not-be-fruitfull effort. Be wary that for most use cases, it might straight up more efficient to look for open source model which have similar properties to what we want in our use cases. If all above passed, move on to the model selection. We need to find a model which inherently well doing on which finetuning technique. We could find a model which work well on full finetuning base or adapter base approach. Finetuning technique selection also need a consideration from the use case and resource we have in hand coupled with the risk of each (full=risk of decay, adapter=risk of can't learn enough). Next step would be preparing the data so it would be suitable to the use case or task (instruct, code, reasoning etc), different use cases and model might have different inherent format of training data such as how they do event token, tooling call, etc, so we need to prepare it accordingly. Tokenize and embedding your data and similar to conventional machine learning, set up your hyperparameter and observability tools.