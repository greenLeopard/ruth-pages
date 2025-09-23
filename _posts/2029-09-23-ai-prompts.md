---
title: AI Promping Notes
description: Notes from the Gen AI course readings
tags:
  - gen-ai
  - google-course
  - prompt-engineering
---
# Gen AI Course: Prompt Engineering

Just a place to make some notes while I'm reading the white pages from [here](https://www.kaggle.com/whitepaper-prompt-engineering).

They are talking about a data format that migt be nice for tracking experiments with prompts and results

## One shot example

```json

{
  "Name": "1_1_movie_classificiation",
  "Goal": "Classify movie reviews as positive, neutral or negative",
  "Model": "gemini-pro",
  "Settings":[
    {"key": "Temperature", "value": 0.1},
    {"key": "Token Limit", "value": 5},
    {"key": "Top-K", "value": null},
    {"key": "Top-P", "value": 1}
  ],
  "Prompt": "Classify movie reviews as POSITIVE, NEUTRAL or NEGATIVE. Review: 'Her' is a disturbing study revealing the diirection humanity is headed if AI is allowed to keep evolving, unchecked. I wish there were more movies like this masterpiece. Sentiment:",
  "Output": "POSITIVE"
  }
```

# Few shot example

Here is a few shot prompt in the table format:

```json
{
  "Name": "1_few_shot_pizza_example",
  "Goal": "Parse pizza orders to JSON",
  "Model": "gemini-pro",
  "Settings":[
    {"key": "Temperature", "value": 0.1},
    {"key": "Token Limit", "value": 250},
    {"key": "Top-K", "value": null},
    {"key": "Top-P", "value": 1}
  ],
  "Prompt": "Parse a customer's pizza order into valid JSON:
    EXAMPLE:
    I want a small pizza with cheese, tomato sauce, and pepperoni.
    JSON Response:
    {
    'size': 'small',
    'type': 'normal',
    'ingredients': [['cheese', 'tomato sauce', 'peperoni']]
    }
    EXAMPLE:
    Can I get a large pizza with tomato sauce, basil and mozzarella
    {
    'size': 'large',
    'type': 'normal',
    'ingredients': [['tomato sauce', 'bazel', 'mozzarella']]
    }
    Now, I would like a large pizza, with the first half cheese and
    mozzarella. And the other tomato sauce, ham and pineapple.
    JSON Response:
    ",
  "Output": "{
    'size': 'large',
    'type': 'half-half',
    'ingredients': [['cheese', 'mozzarella'], ['tomato sauce',
    'ham', 'pineapple']]
    }"
  }

```