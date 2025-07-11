+++
title = "Hackathon project: extracting BigQuery table schemas for use with an LLM"
date = 2025-05-23
draft = false
description = "Short write-up of a CLI tool to extract the schema of any BigQuery table into a text file for use with LLMs."
tags = ['personal projects', 'coding', 'artificial intelligence']
keywords = ['Google BigQuery', 'Rust scripting', 'google cloud api', 'llm usage', 'llm data analysis']
+++
At Uniswap Labs’ biannual onsites, we dedicate most of the week to a company hackathon. It’s a time to think creatively, work on personal projects related to work, and collaborate with others. This time around, I wrote a short script to gather and coalesce BigQuery table schemas into a text document for use with an LLM. An executable, source code, and a usage guide are available on [my Github](https://github.com/mud2monarch/personal-projects/tree/main/uni-schema).

### **The problem to solve**

As part of my work, I regularly use LLMs to help with data queries. We have a broad set of high-quality onchain and offchain data stored in Google BigQuery, and I write SQL to access and transform the data into actionable insights. LLMs — e.g., Claude, ChatGPT — are very helpful for accelerating that work because they help me quickly iterate on my code.

An important part of using LLMs to their max effectiveness is ensuring that your prompt has the necessary *context* for the LLM. Most simply, if you’re asking an LLM to write a SQL query that roughly takes the form of `SELECT (column_names) FROM (table_name)`, you need to provide the LLM the relevant column and table names. If you don’t, you’ll need to edit them manually before running the query, which can be tedious.

### **What I do now**

You could verbally describe the columns and table names, but it’s pretty tedious. Instead, I typically provide the LLM a screenshot of the table schema, which shows the model the column names and their types. However, this has a few drawbacks:

1. Most models only allow four image uploads, so this doesn't work for queries that requires >4 tables, which is common.
2. The model has to “tokenize” the screenshot, which introduces some error vs. text tokenization (I think). This could lead to less accuracy.
3. Images are not “semantically dense” when it comes to the context tokens that they consume. For example, the image of a table schema I tested used 2,205 tokens while the text representation of the table schema used 668 tokens — 33% of the image. If you feed an LLM more tokens than strictly necessary, it will perform worse, all else equal.
4. While small, it takes a little bit of repetitive effort to find and provide the relevant table schema to the model. This is a small, but constant, annoyance.

### **What's better**

A new standard for providing context to models has emerged, the [**llms.txt standard**](https://directory.llmstxt.cloud/). An llms.txt file is essentially a compressed set of documentation, that makes it easier for developers to use LLMs to integrate the API. [**Here is Anthropic’s llms.txt file**](https://docs.anthropic.com/llms.txt). Other AI tools like Cursor use similar concepts — you can define context in a ‘cursor_rules.md’ file that guides the LLM’s output according to your preferences.

### **The Project**

I wanted to write a tool that could programmatically pull schemas for any table in our Google BigQuery into a single text file. The idea would be to feed that single text file into each of my queries so that any LLM I use would have full information about the schemas and table names with which I work.

### **What I made**

Conceptually, [**the script**](https://github.com/mud2monarch/personal-projects/blob/main/uni-schema/src/main.rs) is very straightforward. Google provides [**relatively usable APIs**](https://cloud.google.com/bigquery/docs/reference/rest/v2/tables/get) that help users identify and collect information about Google BigQuery assets — exactly what I wanted to do. At a high level, I:

1. Intake the user’s arguments, which include some config details (credentials, output filepath) and the tables that the user wants to collect (lns. 98-134)
2. Connect to the Google BigQuery API and authenticate (lns. 136-169)
3. Every table in Google BigQuery is defined by a unique `project.dataset.table` identifier, so I iterate through the user’s designated projects, datasets, and tables to collect all table names (lns. 172-266)
4. Collect the schema for every table from the Google BigQuery API (lns. 269-309).
5. Write every schema to a text file, with formatting (lns. 314-374).

For this project, I used the `clap`, `serde`, `reqwest`, and `yup_oauth2` crates for the first time 🙂

And it works! Here’s a demo I made for the hackathon showcase:

{{< youtube ytdzjhRwQzY >}}

### **Reflections**

I’ve already been using this file to accelerate my work. I can more readily chat with the LLM I’m using like I would another employee. Referencing “the blocks table” and specific columns and correcting work in natural language rather than writing SQL myself makes iteration much faster. Here are some reflections on the project:

- Using AI helps you figure out how to use AI better.
- I think the context file I generated could save me up to 40 mins per day on analysis-intensive days (+ a good amount of mental overhead). That's about an 8% increase in productivity (if I worked eight hour days). While that might not sound like too too much, it’s being applied to a base where I'm already 1.7-2x more productive than I was 1.5 years ago. These improvements compound over time
- A 10% productivity improvement for a typical tech employee is equivalent to something like $30k/yr including benefits. Capital investments on internal AI tooling seem well, well worth the cost.
- I like writing Rust! As a beginner engineer, I don’t know all of the errors that I might run into. Writing Rust with robust error handling and strong types *feels* (at the very least) very secure and reliable. When I write and run Python scripts, I often feel like I’m just praying they execute if I return to them a few months later.

*You can use this tool yourself! [Check out the ReadMe and Usage guide for more information](https://github.com/mud2monarch/personal-projects/tree/main/uni-schema).*