---
title: "Picking AI Models for SQL-based Data Analysis With Zaturn"
permalink: ai-models-for-sql-data-analysis
cover_image: picking-models.webp
---

There are many ways to use Zaturn to build an AI for data analysis. You might be using the Claude Desktop App with Zaturn as an MCP, or using an MCP client or AI agent framework where you bring your own LLM API. If you are connecting your own LLM API, you might be running the LLM locally with tools such as [Ollama](https://ollama.com), using the LLM developer's official API, or using a 3rd party LLM API aggregator such as [OpenRouter](https://openrouter.ai/) or [LiteLLM](https://www.litellm.ai/). In every case, there is an important decision to be made: which LLM do you use? In this blog, I try to break down the factors involved in picking an LLM for a data analysis agent.

## Cost

Quite obviously, the cost is the most important factor that can make or break a use case for an AI application. The cost itself depends on various other factors, such as the organization that developed the LLM, domain knowledge coverage, languages, and other features such as tool calling abilities. The best way to reduce costs is to find models that have exactly the features we need for data analysis, and do not have the features we do not need.

The features you surely need: 
- Good tool calling abilities
- Programming (specifically SQL for Zaturn)
- Thinking & Reasoning.

The features you might need:
- Image input: If you want the AI to comment on generated images
- Multilingual support: If you or your users want to prompt in languages other than English

The features you mostly don't need:
- Vast domain expertise

In the following sections, let's look at some of these factors and the most cost-effective models for each factor.

## Programming Abilities

Data analysis involves writing code to crunch numbers. Unless AI models are good at that, they will not be of much use. So it's best to pick models that are good at writing code based on human instructions. With Zaturn, data analysis happens through SQL code, which hasn't changed much in recent years as much as Python or NodeJS frameworks, syntax, and best practices keep changing. So you could cut some costs by choosing an older model, if that is an option.

The following are some models that work best for programming:
- GLM 4.5 by z.ai
- Qwen3 Coder by Qwen
- Kimi K2 by MoonshotAI
- Gemini 2.5 Flash by Google

Finally, some models that aren't optimized for programming still work decently well with SQL, as SQL is not as complex as other languages. So the models listed above aren't your only options.

## Tool Use

Zaturn or any other framework that helps LLMs analyze data is bound to work by providing tools to the LLM, which it can use to query the data it needs to query in order to reply to user prompts. So, tool-use ability is a make-or-break criterion while picking an LLM for data analysis. The following are some cost-effective AI models for which I've seen decent performance with Zaturn:

- Gemini 2.5 Flash Lite by Google
- GLM 4.5 by z.ai
- Grok 3 Mini by xAI
- GPT-4.1 Nano by OpenAI

## Open Source / Self-hostability

The Zaturn project is open source and not a SaaS. One of the key advantages of this is that the tools can run locally or on-premises - your database URLs and files aren't shared with anybody else. The only data that ever goes to a 3rd party is the conversations you have with the LLM, and the data pulled up during the tool usage in these conversations. If you self-host the LLM on your premises, then absolutely no data will be sent to any 3rd party - your full AI-based data analysis stack remains on premises.

Here are some self-hostable models that work best for data analysis:
- GLM 4.5 by z.ai
- Qwen 3 32B by Qwen

Some folks also self-host AI models with the intention of reducing the carbon footprint produced by power-hungry GPUs. While this works well for lightweight models that can run on commodity hardware CPUs, having a GPU at home does not necessarily make the approach any greener. In fact, data center GPUs typically are under centralized power use optimizations, while having a powerful GPU at home might actually be a misuse of electricity supplied for domestic purposes.

## Context Window

Each LLM has a context window that ranges anywhere from a meagre 4K tokens to more than a million tokens. When the context window runs out, a new conversation has to be started, and the LLM will not have any context of the previous messages in the old conversations. 

For data analysis tasks, LLMs with smaller context windows cannot do much more than write one or two SQL queries after being presented with a table structure and a prompt. The conversational/agentic experience is lost, and it's only as good as an SQL autocomplete tool. 

From my experience, I'd recommend a context window of at least 128K when you're asking a specific question about your data. This will leave some room for follow-up questions too. Further, a context window of 1M tokens works amazingly well for in-depth exploratory data analysis. You can let an LLM loose on your data with a prompt like "Here's all the data from our business, go through it in detail and give us a department-wise action plan for the next quarter." The LLM can then run a handful of queries and summarize the results for you, keeping all the results in context together.

Here are some LLMs with high context windows (1M+ tokens) that work well for data analysis:

- Gemini 1.5, 2, and 2.5 series by Google
- GPT-4.1 and variants by OpenAI
- Qwen Turbo by Qwen

## Thinking & Reasoning

Answering questions using data often involves planning, drafting a series of SQL queries, running them, getting results, and summarizing the results into a concise, useful insight for humans. Models with reasoning and thinking abilities are able to do this effortlessly with a separate budget for "reasoning tokens".

Models that cannot do this have to be prompted for each step, like "Step 1: Get the orders from the Orders table grouped by Customer; Step 2: Join this with the Customer table and get an aggregate of orders grouped by Customer country." A model with reasoning abilities can work with a simple prompt, "Which countries are generating the most revenue for us?". It will automatically go through any table as necessary, perform joins, and produce the required results. If any step fails, the AI will automatically understand what went wrong and try alternative approaches. It can do a lot more with just one prompt.

## Multimodality

Data analysis isn't just text - it involves a lot of visualizations that are images and sometimes even animated GIFs. Zaturn itself includes tools for generating visuals. LLMs operate with different input and output modalities, such as text, audio, image, and video.

For data analysis, only text as an output modality is sufficient for most use cases, as the visuals are generated by the tools and not by the AI model. For input modalities, text works for number crunching and generating verbal insights, while the image input modality is useful to help the AI see and comment on the visuals it generates through tool use. Audio as an input/output modality can help you "talk" to the data analysis agent and add to the coolness factor.

## Conclusion

In this blog, we went over the different factors to consider while picking an LLM to work with data as a data analysis agent. Tool-use capabilities, context-window size, and reasoning abilities are the crucial factors that can make or break your experiences. Most models that are good with tool use are fairly decent at writing SQL, so this factor is not much of a separate consideration.

Considering these factors and cost as well, Gemini 2.5 Flash Lite by Google would be my top recommendation. It costs $0.10 / 1M input tokens, $0.40 / 1M output tokens, and supports image inputs as well. The only downside is that it's not self-hostable. Among the self-hostable models, my current recommendation would be GLM 4.5 by z.ai.

