# OpenAI o3 model vs o1 model reasoning ability comparison and My Prediction

Hi, in this blog, I will introduce you some of my analysis on the OpenAI's reasoning model o3 capabilities improvement over OpenAI o1 models.
In Dec 2024 OpenAI's product and model releases, the last day's model release o3 is the most attractive. And I am wondering what's the difference between o1 and o3 model 
and what's are implication of the research path for the future. And here is what I have in mind: 

## 1. OpenAI O3 Reasoning as Short-Cut Learning

If we visualize the reasoning sampling process as a tree:

On the left side is the shortcut learning (Short-Cut Learning) we pursued in the past: reaching the correct result with the fewest steps. On the right side is the 'reflection and backtracking' paradigm represented by OpenAI O1.

We know that during the search process in O1, the model constantly reflects and backtracks, and this process often comes with additional costs. The question is, if the model can give the correct answer in one go, who would still want to spend time and money on complex searches? OpenAI isn’t foolish; everyone knows shortcuts are better!

For more difficult problems, the potential thought tree becomes wider, and the search space at each step grows larger. The probability of reaching the correct answer via a shortcut becomes smaller. So, what can be done? An intuitive approach is to prune! Cut off the tree nodes that are unlikely to reach the endpoint in advance, compressing the search space—narrowing the tree back down. This is also the direction of many current efforts, for example:

Chain of Preference Optimization naturally constructs preference data from the thought tree and uses DPO to optimize it, increasing the likelihood that the model will select tree nodes that can reach the endpoint. Outcome-supervised Value Models treat reasoning as an MDP process, using the probability (value) of reaching the correct answer at each step to guide strategy optimization.


## 2. Tree Search vs CoT Search

Back to O1, why choose to break away from the traditional shortcut approach and go down the 'detour' of Tree Search?

In the past, we tended to exploit the basic capabilities of the model, and we believed that the existing GPT-4 model could already meet most conversational and simple reasoning needs. These tasks could be effectively sampled, preference-graded, and iteratively optimized.

However, this perspective overlooks the needs of more complex tasks—such as mathematical reasoning (AIME, Frontier Math), code generation (SWE-Bench, CodeForce), and others. These tasks are often difficult to yield returns in the short term—they have very sparse rewards, only revealing rewards when the correct answer is eventually reached.

Therefore, the traditional shortcut learning approach is no longer suitable for handling such complex tasks: if you can’t even sample a correct path, how can you optimize the model to select the right path?

Returning to the 'Monte Carlo mindset' in the title of this article, we can see that this is essentially the same thing: the application of the Monte Carlo method in reinforcement learning is based on repeatedly sampling to estimate the value of a strategy, thereby optimizing the model. However, this method has inherent limitations—if the sampled strategies cannot find the optimal path, the model’s optimization will always end up with only a local optimum. This is why we choose more exploratory strategies in MC Learning.


## 3. Reasoning Capability improvement from o1 model to o3 model

Before the release of O3, some people could imagine that the reasoning tokens of the O-series models would continue to increase. Following the previous pattern, there was an expectation that the increase would follow an empirical formula, improving by a certain multiple every few months. However, the information about O3 truly shocked everyone. In just 3 months, the inference cost increased by 2-3 orders of magnitude.

In light of this result, I admit I had previously underestimated the speed of progress in the software field. Unlike chips, which are limited by manufacturing processes, physical conditions, and other factors, software can quickly consume all available hardware resources.

Experienced engineers know that even for software solutions, when facing an increase in scale by several orders of magnitude, it’s not that easy. Often, each time the scale triples, new problems arise. O3’s ability to increase inference scale by more than 2 orders of magnitude so quickly is certainly not due to OpenAI’s exceptional team solving a lot of problems one after another in multiples of three.

There are very few solutions that can quickly scale inference like this. The most typical ones involve various exploratory algorithms, where brute-force exploration can consume a lot of computation power, but the implementation is not that complicated. From simple breadth-first search to Monte Carlo Tree Search (MCTS), they all exhibit this characteristic.

It’s reasonable to believe that O3 implements multi-path reasoning. Conversely, I don’t think O3 could extend the reasoning length by more than 2 orders of magnitude with single-path reasoning while maintaining consistent performance.

When o1-preview was first released, I wrote a technical analysis of the O1 model, pointing out that the O1 series likely uses single-path reasoning. To this day, I still believe that’s the case. However, I currently don’t have a confident guess about the reasoning_effort parameter.

But o1 Pro mode seems different. Its CoT summarization performance doesn’t appear to be the same as O1. My current observations aren’t sufficient yet to confidently make a guess based on its performance. I hope the O1 Pro mode API will be released soon.

As for o3, it seems to use some form of multi-path reasoning, although it’s unclear exactly how these multiple paths are generated.

Currently, there are two unexplained aspects of o1: the o1 model API cannot control the temperature, and the reasoning tokens of O1 are always multiples of 64."


## References

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

