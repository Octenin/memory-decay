# Memory Decay
### What if AI could learn when to forget?

I've been thinking a lot about AI memory lately, particularly how much information AI systems should retain, how long they should retain it, and whether remembering everything is necessarily a good thing.

Human memory is far from perfect. We forget things, sometimes important things, and occasionally remember things incorrectly. But forgetting also serves a purpose. It helps us prioritize information, make room for new experiences, and move on from things that may no longer be relevant.

That got me wondering: **What if AI memory worked a little more like ours?**

Memory Decay is a small experiment exploring that question.

## The Idea

AI systems can store information about users and retrieve it later. Depending on how they're designed, that information might remain available long after it was originally shared.

But people change.

A preference someone mentioned six months ago might no longer be relevant. A goal they were working toward last year might have been abandoned. Something they said during a particularly difficult week shouldn't necessarily define how an AI interacts with them indefinitely.

I wanted to explore whether a system could account for that.

Instead of treating every stored memory as equally relevant forever, what if memories gradually became less influential unless they were reinforced?

And what if that process could encourage an AI to ask questions rather than make assumptions?

## How It Works

The experiment draws inspiration from the **Ebbinghaus forgetting curve**, a model describing how human memory retention can decline over time.

I adapted that general idea into a simple mathematical model for simulated AI memories.

Each memory has several properties:

- **Memory type:** Whether it's a fact, preference, goal, event, or temporary context.
- **Initial confidence:** The starting value assigned to the memory.
- **Decay rate:** How quickly its score decreases over time.
- **Reinforcement count:** How many times the memory has been reinforced.
- **Last reinforced:** When the memory was most recently reinforced.

Different memory types decay at different rates.

For example, a relatively stable personal fact might decay slowly, while temporary context from a conversation might lose relevance much faster.

Reinforcement slows the decay process, allowing frequently revisited information to remain influential for longer.

### The Formula

The experiment uses exponential decay:

```text
confidence = initial_confidence × e^(-adjusted_decay_rate × hours_elapsed)
```

The decay rate is adjusted according to reinforcement:

```text
adjusted_decay_rate = base_decay_rate / (1 + 0.3 × reinforcement_count)
```

The numbers are experimental parameters, not scientifically validated settings for AI memory.

They're intended to demonstrate how different memory behaviors might work.

## Try the Interactive Demo

**[Launch Memory Decay](https://octenin.github.io/memory-decay/)**

The demo lets you explore five different types of simulated memories.

You can advance time by a day or a week, reinforce individual memories, and watch how their scores change.

You'll notice that some memories fade relatively quickly, while others remain influential for much longer.

You can also open `index.html` locally in your browser. No installation or additional dependencies are required.

## When Should AI Ask Instead of Assume?

One of the questions behind this project is whether AI systems should become more comfortable acknowledging uncertainty.

Imagine telling an AI assistant that you're planning to move to another city.

A year later, should it still assume you're moving?

Or would it be better to ask whether that's still the plan?

In this experiment, memories fall into different categories as their scores decline:

| Simulated score | Suggested behavior |
|---|---|
| 70% or higher | Use the memory without an additional verification prompt |
| 50–69% | Use cautiously |
| 30–49% | Ask the user to verify |
| Below 30% | Mark the memory as archived |

These thresholds are illustrative. They are not established safety standards, and a high score doesn't mean the underlying information is correct.

For sensitive or consequential information, verification may be appropriate regardless of the score.

## What This Experiment Doesn't Do

This is a proof of concept, not a complete AI memory system.

The demo uses predefined example memories and simulated time progression. It doesn't connect to a language model, learn from real conversations, or evaluate whether stored information is accurate.

There's also an important distinction between **memory decay and factual confidence**.

The score in this project represents a modeled decline in a memory's influence over time. It doesn't measure the probability that a statement is true.

Something someone told an AI yesterday could be incorrect. Something they shared five years ago could still be completely accurate.

Time alone can't resolve that distinction.

I think that's one of the more interesting limitations of this approach, and something worth exploring further.

## Why I'm Interested in This

My interest in AI extends beyond what these systems can accomplish technically. I'm equally interested in how they interact with people and what responsibilities come with increasingly capable technology.

Memory is a particularly interesting part of that conversation.

How much should AI remember about us? Who gets to decide what's important? Should users have the ability to correct, reinforce, or permanently remove memories?

And how do we build systems that are useful without becoming unnecessarily intrusive?

I don't think making AI more human-like is automatically the answer. Human memory has plenty of limitations of its own.

But I do think there's value in exploring whether some of the principles behind human memory could help us design AI systems that are more thoughtful about the information they retain and use.

## Where I'd Like to Take It

There are several questions I'd like to explore as this project develops:

1. Could memory relevance be evaluated using more than elapsed time and reinforcement?
2. How should an AI distinguish outdated information from information that's simply old?
3. Could users have more meaningful control over what an AI remembers?
4. How should memory systems handle sensitive information?
5. Could better memory management reduce the likelihood of AI making confident but outdated assumptions?

I’m particularly interested in the relationship between memory, uncertainty, user autonomy, and trust.

## Technical Details

The interactive demonstration is built using HTML, CSS, and JavaScript.

It runs entirely in the browser and doesn't require a backend or external API.

The current implementation includes:

- Five simulated memory categories
- Exponential decay calculations
- Reinforcement-based decay adjustments
- Simulated time progression
- Memory score thresholds
- Visual indicators for memories requiring verification
- Light and dark display modes

## A Final Thought

I started this experiment with a fairly simple question: What if forgetting could actually make AI better?

I don't know whether this particular approach is the right one. There are plenty of limitations, and the relationship between memory, relevance, and accuracy is much more complicated than a mathematical curve.

But that's part of why I wanted to build it.

Sometimes the most interesting part of an experiment isn't proving an idea works. It's discovering which questions you hadn't thought to ask.

---

*An independent experiment exploring AI memory, uncertainty, and human-centered technology.*
