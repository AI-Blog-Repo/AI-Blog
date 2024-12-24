# OpenAI o1 model reasoning capabilities analysis and possible model architectures

## Introduction
In this blog, I will try to make my assumptions and analysis of which AI technology and roadmap OpenAI is using to improve the o1 series model's reasoning capabilities. Since OpenAI released the o1 model and gains significant improvement on the science, coding, and math ability (https://openai.com/index/introducing-openai-o1-preview/), a lot of guess are propose on how did they make the model improvement? Some possible guesses include self-play reinforcement leanring, Chain-of-Thought, etc. So here is my list of possbile techniques that OpenAI is using to improve the reasoning ability of o1 series model.


### Table of Contents
#### Possibility 1: Chain of Thought(CoT) + RL
#### Possibility 2：Automatic Cot+Prompt Improvement
#### Possibility 3：Supervision in the process other than Supervision from Results
#### Possibility 4：Post-Training (Test-Time) Scaling Laws
#### Possibility 5：Self-Play Reinforcement Learning



## Possibility 1: Chain of Thought(CoT) + RL
The value of reinforcement learning has once again been validated. To make a model that failed to understand recursion during the pre-training phase learn to think recursively, reinforcement learning is an excellent method. AlphaGo used reinforcement learning to continuously play against itself, and ultimately, AlphaGo's ability far surpassed that of humans. Some people believe that reinforcement learning, with self-play, is only useful for games with clear win/loss outcomes, and has little relevance to training large models. I believe that as long as the objective function is defined, such as with mathematical and programming problems where right and wrong are relatively easy to judge, large models can also learn using strategies similar to AlphaGo’s. When Noam Brown switched to OpenAI in 2023, he mentioned that reinforcement learning could increase GPT-4's reasoning ability by 1000 times, and I strongly agreed with him. Just four months later, the mysterious Q* was developed. A year later, today, the O1 model was officially released. In OpenAI’s O1 technical blog, it says: 'Similar to how humans think for a long time before answering a difficult question, O1 uses a 'chain of thought' when attempting to solve problems. Through reinforcement learning, O1 has learned to refine its chain of thought and optimize the strategies it employs. It has learned to identify and correct mistakes, break down complex steps into simpler ones, and try different approaches when the current method fails. This process has greatly enhanced the model's reasoning ability.


## Possibility 2：Automatic Cot+Prompt Improvement

Allowing the model to automatically learn the chain of thought during the training phase, without manual intervention, enables it to break down and answer large problems.

The above process has a major flaw, which is the need for a large amount of manual writing of COT rules. This may work for certain types of problems, but it is clearly not feasible to write derivation logic for every problem. Therefore, OpenAI has drawn on AlphaGo’s MCTS and reinforcement learning methods, enabling LLMs to quickly find the CoT path, and this process does not require manual intervention—allowing the model to automatically generate it.


## Possibility 3：Supervision in the process other than Supervision from Results

Allow the model to no longer learn from result data, but to learn the thinking process of each step, just like humans.



## Possibility 4：Post-Training (Test-Time) Scaling Laws

This means that AI learning is no longer limited to the pre-training phase. It can also use the exploration time from RL training during the inference phase, and increase the model's thinking time to improve performance.


## Possibility 5：Self-Play Reinforcement Learning

The o1 model is trained using Self-Play Reinforcement Learning (Self-Play RL), a training method applied in reinforcement learning. Simply put, the agent optimizes its strategy by interacting with its own copy or past versions. The core idea is to have the agent continuously play against itself to accumulate experience and improve its performance. Self-play RL is not a very new method—AlphaGo and AlphaZero, years ago, used this approach to surpass human-level Go playing. In addition, Self-play RL is widely applied in various fields, such as training AI opponents in competitive games and multi-agent systems. Recently, this method has been used to train AI to play atari games, and it turned out to be quite impressive.

In the process of training large models, humans have almost exhausted existing human knowledge. We provide datasets, feedback, and labeled information, but large models do not “discover” the patterns behind language through independent exploration. Instead, they directly extract valuable information from the materials we provide, like memorizing. So what if there’s no more material to memorize? This requires a new approach to break the deadlock. During the Self-play RL process, data can be generated automatically without manual labeling (which, in fact, is impossible for reasoning tasks), which greatly reduces the data anxiety of researchers. However, just using RL alone is not enough to achieve the results demonstrated by the o1 model. We also need another powerful tool: Chain of Thought (CoT). CoT is not exactly a new concept; we use it when writing prompts. In simple terms, it involves solidifying human thought processes step by step and breaking down complex problems into simpler ones that are easier to solve. But when the o1 model combines CoT with Self-play RL, a “miracle” happens—the model demonstrates an exceptional ability for self-improvement and error correction! This has never been seen in any previous large model!

OpenAI researchers shared a classic moment of “self-reflection” in the o1 model. Regarding this change, OpenAI even provided the most suitable prompt guidelines for o1. In general, the guidelines suggest that prompts should be simpler and more concise, advocate for using separators to enhance readability, and avoid the “step-by-step prompts” used previously, since o1 can do that on its own. When providing additional information or documentation, only the key points directly related to the question need to be included. Moreover, the o1 model has made the “chain of thought” transparent—users can see how the model gradually reasons to arrive at a result. Undoubtedly, this helps improve the model's interpretability, making it easier for people to trust it.

In demonstrating the chain of thought, the o1 model hides the most original version. What we see is the version aligned with safety guidelines. Compared to previous models, o1 is better at resisting the generation of harmful content. In “jailbreak tests,” o1’s score is 4 times that of GPT-4, proving that it can better understand and apply safety rules within the context.

“Usable” AI Agent
Current agents still require external guidance when handling complex tasks, and the results of single-step executions are not reliable enough. It can be anticipated that foundational models like o1, with strong multi-step reasoning abilities, will significantly improve the reliability of agents executing tasks. AI agents will learn strategies and optimize decisions through continuous trial and error, without external guidance. Since the o1 model has already shown great potential in fields such as physics, chemistry, and biology, it will undoubtedly unlock new application scenarios, such as annotating cell sequencing data, generating complex mathematical formulas, and building multi-step workflows. These scenarios will eventually converge into various agents. With further improvements in model accuracy and reliability, the usability of agents will reach a critical point for industrial-scale deployment, likely leading to broader applications across multiple industries, including manufacturing, urban governance, healthcare, and more. Additionally, as mentioned above, the o1 model has also explored and practiced improving the safety of AI applications, which further provides security guarantees for AI agents in critical fields.


## Related Reference

#### AI Agent Marketplace and Search
[AI Agent Marketplace and Search](http://www.deepnlp.org/search/agent) <br>
[Robot Search](http://www.deepnlp.org/search/robot) <br>
[Equation and Academic search](http://www.deepnlp.org/search/equation) <br>
[AI & Robot Comprehensive Search](http://www.deepnlp.org/search) <br>
[AI & Robot Question](http://www.deepnlp.org/question) <br>
[AI & Robot Community](http://www.deepnlp.org/community) <br>
##### AI Agent
[AI Agent Reviews](http://www.deepnlp.org/store/ai-agent) <br>
[AI Agent Publisher](http://www.deepnlp.org/store/pub?category=ai-agent) <br>
[Microsoft AI Agents Reviews](http://www.deepnlp.org/store/pub/pub-microsoft-ai-agent) <br>
[Claude AI Agents Reviews](http://www.deepnlp.org/store/pub/pub-claude-ai-agent) <br>
[OpenAI AI Agents Reviews](http://www.deepnlp.org/store/pub/pub-openai-ai-agent) <br>
[AgentGPT AI Agents Reviews](http://www.deepnlp.org/store/pub/pub-agentgpt) <br>
[Saleforce AI Agents Reviews](http://www.deepnlp.org/store/pub/pub-salesforce-ai-agent) <br>
[AI Agent Builder Reviews](http://www.deepnlp.org/store/ai-agent/ai-agent-builder) <br>
##### AI Reasoning Chatbot
[OpenAI o1 Reviews](http://www.deepnlp.org/store/pub/pub-openai-o1) <br>
[OpenAI o3 Reviews](http://www.deepnlp.org/store/pub/pub-openai-o3) <br>
##### AI Video Generation
[Sora Reviews](http://www.deepnlp.org/store/pub/pub-sora) <br>
[Kling AI Reviews](http://www.deepnlp.org/store/pub/pub-kling-kwai) <br>
[Dreamina AI Reviews](http://www.deepnlp.org/store/pub/pub-dreamina-douyin) <br>
[Best AI Apps Review](http://www.deepnlp.org/store/pub) <br>
[AI Video Generator](http://www.deepnlp.org/store/video-generator) <br>
[AI Image Generator](http://www.deepnlp.org/store/image-generator) <br>
[AI Glasses Review](http://www.deepnlp.org/store/ai-glasses) <br>
[VR Glasses Review](http://www.deepnlp.org/store/vr-glasses) <br>
##### Robotics
[Tesla Cybercab Robotaxi](http://www.deepnlp.org/store/pub/pub-tesla-cybercab) <br>
[Tesla Optimus](http://www.deepnlp.org/store/pub/pub-tesla-optimus) <br>
[Figure AI](http://www.deepnlp.org/store/pub/pub-figure-ai) <br>
