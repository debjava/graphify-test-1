Execute the commands in the order

Install pipx
py -m pip install --user pipx

or

python -m pip install --user pipx

Add pipx to your PATH

py -m pipx ensurepath

pipx --version  or  py -m pipx --version

Setup graphify
==============

`pipx install graphifyy`

graphify --version

graphify install

graphify install --platform cursor

keep the source code base diectory in the same directory.

Execute the below command.

graphify .

you might get the following

error: no LLM API key found (18 doc/paper/image file(s) need semantic extraction). Set GEMINI_API_KEY or GOOGLE_API_KEY (gemini), MOONSHOT_API_KEY (kimi), ANTHROPIC_API_KEY (claude), OPENAI_API_KEY (openai), DEEPSEEK_API_KEY (deepseek), or pass --backend. A code-only corpus needs no key. Or pass --code-only to index just the code (local AST, no key) and skip the non-code files.


Execute the below commands

graphify extract . --code-only

graphify cluster-only . --no-label

graphify export html

graphify explain "CodeSharingUtil.java"

References
==========
https://docs.graphify.com/quickstart

https://docs.graphify.com/integrations/claude-code

Usages of graphify
======================
Yes! You can use graph.json with both Claude Code and OpenAI Codex to help identify bugs in your code repository. However, the best approach is to let the AI assistant use the graph to understand code relationships and then inspect the actual source code to find the bug.

Graphify supports this kind of workflow, including querying relationships and tracing paths between components.

Let me show you how to do it practically.

1. How does it help identify bugs?

Suppose your Python repository contains the following files:

my-project/
├── main.py
├── order_service.py
├── payment_service.py
├── database.py
└── graphify-out/
    ├── graph.json
    ├── graph.html
    └── GRAPH_REPORT.md

Imagine your application has this bug:

The order is marked as successful even when the payment fails.

The problem might involve multiple functions across different files.

Without Graphify, the AI assistant needs to investigate the source code and determine how these functions interact.

With Graphify, it can first explore the relationships:

create_order()
      |
      v
process_payment()
      |
      v
payment_status
      |
      v
update_order_status()

The graph helps the AI identify where to investigate. The source code then helps it determine whether the payment result is handled correctly.

Important: This is an illustrative graph. Graphify will only expose relationships it successfully extracts or infers from your actual repository.

2. Method 1: Give the graph to Claude Code or Codex

You can start with a simple approach without configuring anything complicated.

Step 1: Open your project

Open Claude Code or Codex in your repository's root directory.

Make sure the repository contains:

Your source code.
graph.json.
GRAPH_REPORT.md.
Step 2: Ask the AI to investigate a bug

Try this prompt in Claude Code or Codex:

Bug Investigation Prompt

I have generated a Graphify knowledge graph for this repository.

Please use the following files to understand the architecture:

graphify-out/GRAPH_REPORT.md
graphify-out/graph.json

I want you to identify potential bugs in this repository.

Follow these steps:

Understand the main components and their relationships using the Graphify report and graph.
Trace the execution flow of important functions.
Inspect the actual source code associated with those functions.
Look for logical errors, incorrect error handling, missing validations, and incorrect handling of dependencies.
Identify the exact file and line number for each potential bug.
Explain how the bug occurs and provide a reproducible scenario if possible.
Suggest a fix for each confirmed bug.

Do not assume that a relationship in the graph proves a bug exists.
Verify every finding against the actual source code.

Distinguish confirmed bugs from potential issues, and do not modify any files until I approve the proposed fixes.

What happens next?

The assistant can use the graph as additional context, investigate the relevant source files, and explain its findings.

One limitation: merely mentioning graph.json in a prompt does not guarantee that the assistant will query it effectively. The assistant needs access to the file and suitable instructions or tools to use its contents.

3. Method 2: Query Graphify before asking the AI to investigate

This is a more effective approach because you don't need to provide the entire graph as context.

Graphify provides commands for querying the graph, tracing paths, and explaining individual nodes.

For example, run these commands in your project terminal:

Understand the payment flow:

graphify query "Show the payment processing flow" --graph graphify-out/graph.json

Trace the relationship between payment and order status:

graphify path "process_payment" "update_order_status" --graph graphify-out/graph.json

Inspect a particular function:

graphify explain "process_payment" --graph graphify-out/graph.json

These are examples based on the documented Graphify CLI. The names must match entities in your graph, and exact command support can depend on your installed version.

Review the results, then ask Claude Code or Codex:

Using the Graphify results, investigate whether the order status can be marked successful when payment processing fails. Inspect the relevant source files, identify the root cause, and suggest a minimal fix.

This workflow is useful because the graph helps narrow down which parts of the repository deserve attention.

4. Method 3: Make Claude Code or Codex use Graphify automatically

If you plan to use Graphify regularly, you can configure your AI coding assistant to consult the graph when investigating your codebase.

Graphify documents platform-specific setup commands.

For Claude Code, run:

graphify claude install

For Codex, run:

graphify codex install

Run the appropriate command from your project directory.

These commands configure the respective assistant to use Graphify as part of its codebase investigation workflow. The exact integration mechanism differs between the two assistants.

After setup, you can ask questions such as:

Find potential bugs in the payment processing flow.
Trace the dependencies of the authentication module.
Identify components that could be affected by a database change.
Investigate why a particular API returns an incorrect result.

The assistant can use the graph to navigate the repository before examining the relevant source code.






