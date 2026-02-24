# Browser Agent

This is a browser automation agent that lets you give a task in plain English and watches an AI carry it out in a real browser window. You type something like "find the cheapest flight from Stockholm to London next Friday" and the agent takes screenshots, figures out what to click, and works through it step by step until the task is done or it hands control back to you.

## How it works

The agent takes a screenshot of the current browser state and sends it to GPT-4.1 along with your instruction. The model looks at the screenshot and decides what to do next, whether that is clicking, typing, scrolling, or pressing a key. The agent executes the action, takes another screenshot, and sends it back. This loop continues until the model decides the task is complete.

You stay in the loop. If the model hits a safety check that requires human confirmation, it pauses and asks you before continuing.

## How to run it

Copy the environment template and fill in your Azure keys.

```
cp .env.example .env
```

Install the dependencies.

```
pip install openai playwright python-dotenv
playwright install chromium
```

Run the agent.

```
python agent.py
```

A browser window opens. Type your task when prompted. Type `exit` to quit.

## Source

This implementation is adapted from the official Microsoft documentation for the Computer Use preview model.

* [Computer Use in Azure OpenAI (Microsoft Learn)](https://learn.microsoft.com/en-us/azure/foundry-classic/openai/how-to/computer-use?tabs=python)