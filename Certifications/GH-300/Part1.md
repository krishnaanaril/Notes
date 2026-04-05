# GitHub Copilot Fundamentals - Part 1

- Six core principles of responsible AI:
    - Fairness
    - Reliability and safety
    - Privacy and security
    - Inclusiveness
    - Transparency
    - Accountability
- “AI must be FR‑PITA to misuse” — if it’s not FRPITA-compliant, it’s a problem.
- Subscription Plans:
    - Free, Pro, Pro+, Business, Enterprise
- Core rules for creating effective prompts:
    - Single: Always focus your prompt on a single, well-defined task or question. This clarity is crucial for eliciting accurate and useful responses from Copilot.
    - Specific: Ensure that your instructions are explicit and detailed. Specificity leads to more applicable and precise code suggestions.
    - Short: While being specific, keep prompts concise and to the point. This balance ensures clarity without overloading Copilot or complicating the interaction.
    - Surround: Utilize descriptive filenames and keep related files open. This provides Copilot with rich context, leading to more tailored code suggestions.
- “Write prompts using the 4S rule — Single, Specific, Short, and Surround.”
- Maintaining long conversation histories can become inefficient and costly in terms of processing.
- How to keep PRU usage low
    ✅ Summarize context explicitly
    ✅ Reset conversations when switching tasks
    ✅ Avoid unnecessary chat history
    ✅ Be Single, Specific, and Short
- Role prompting involves instructing GitHub Copilot to act as a specific type of expert, which can significantly improve the quality and relevance of generated code for specialized domains. This approach helps accelerate development by getting more targeted solutions on the first try.
- Code Editor <-> Proxy Server/Toxicity Filter <-> LLM
- You should be mindful of context window limitations when crafting prompts. Breaking down complex problems into smaller, more focused queries or providing relevant code snippets can significantly enhance the model's ability to provide accurate and helpful responses.
- Fine-tuning is a critical process that allows us to tailor pretrained large language models (LLMs) for specific tasks or domains. It involves training the model on a smaller, task-specific dataset, known as the target dataset, while using the knowledge and parameters gained from a large pretrained dataset, referred to as the source model.

## Introduction to Copilot Spaces
- Use a Space when you want consistent, reproducible answers on a tightly scoped topic, like a particular service, a runbook or playbook, or a known dataset. Compared to general or repo‑wide chat, Spaces trade breadth for depth: by narrowing the context to what matters most, they tend to produce more predictable, grounded responses, while broad chat can surface wider discovery but may be less precise.
- Once named and configured, it (Copilot Space) becomes a reusable workspace where Copilot operates within a clearly defined scope. 

## Using advanced GitHub Copilot features

- Visual Studio Code has a feature called agents that allows you to interact with GitHub Copilot. These agents allow you to ask questions using a specific context. For example the `@terminal` agent helps you chat with GitHub Copilot to interact with the terminal.
- Premium models consume 2 PRUs per request - double the standard rate.
- The content exclusion feature in GitHub Copilot helps protect sensitive information by preventing the use of specific files, directories, or repositories to inform code-completion suggestions.
-  In Visual Studio Code and Visual Studio, content exclusions are not applied when you use the @github chat participant in your question.