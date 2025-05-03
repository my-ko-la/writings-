
# Disclaimer 

This article is brought to you by organic, pure-bred thought and subjective rationality - no AI tools were used to articulate, edit, influence, or in any form interact with the contents of the article.

# Introduction 

Throughout my comparatively short programming career I have had the pleasure to experience how unlike any other discipline programming, or, perhaps more appropriately, software engineering [[EDIT: why is it more appopriate]] is different from any other activity I have attemped before.

It has the capacity to bring intense feelings of joy and satisfaction, not only from the problem solving, but from the struggle, the challenge, the growth. I have been pretty lucky to work with talented developers, from whom I have learned a lot. XX_random?

The discipline, however, is far from a tranquil walk in the park. It can drain you, mentally and emotionally. On numerous occasions I have experienced the exhaustion that comes from thinking about a problem for hours on end, only to discover the answer seemingly on a whim the next day (surprisingly, quite often while being in a room that has all the properties of a bathroom) [[EDIT: this joke can be made better]]. 

It makes you keenly aware of your shortcomings, whether they are in faulty reasoning, misunderstood requirements, a lack of education, unused systems thinking, interactions with time management - the list is long. 

You get better at recognizing these shortcomings, you get faster at overcoming them, to the point where they do not require active cognitive attention, and are essentially baked into your logic when designing and developing software. Yet, you still find yourself making errors, ranging from a simple "I left a typo in the log" oopsie to a production-breaking fucky-wucky.

## So, why the yapping?

With this article, I want to distill and, as neatly as is possible for me, externalize my thoughts and share my current approach to problem solving. 
I want to sprinkle some tidbits of knowledge and concepts that I find to be the most bang for your buck, as they were for me.

I am not pretending to have introduced a Revolutionary New Paradigm, what you will read (thanks, btw) below is embarrasingly self-evident. 

# How I tackle problems: Trace-Validate-Test

TVT is an intentionally minimal, expressive set of questions. You can think of it as a structured reasoning operator over any step, assumption, or decision. 

## Trace 

TRACE is the step that asks "how did we get here?". It is an interrogation of the origin, taking stock of the assumptions that are baked in, making sure we understand the supporting context and the environment in which the decision was made. The goal is to get a grip on the roots of the current structure. Some of the questions that you can ask yourself: 

- Where did this idea/step/assumption come from, and what supports it?

- Is this step derived from a spec, a guess, a heuristic, or an external constraint?
    
- What prior knowledge or context am I using here?
    
- What assumptions am I smuggling in?
    
- If this is a structural decision, what’s its _origin schema_?

## Validate

VALIDATE asks: "is this step _necessary_, _minimal_, and does it preserve the problem’s _invariants_?"

We want answers to the following: 

 Is this the simplest expression of the idea?
    
- Is it necessary, or just familiar?
    
- What invariants does this step enforce or violate?
    
- What failure modes exist? Can I create an illegal state?

The objective is to determine whether the step is overfit, incomplete, or unsafe for all valid inputs and states. 

## Test

TEST looks to understand the propagation of the decision, its sytemic consequences. 

- What first-order and second-order effects emerge from this step?
    
- What other parts of the system become dependent on it?
    
- What does this coupling force downstream?
    
- What’s the _cost of change_ if this step turns out to be wrong?

We want to figure out the blast radius of the decision, see how system topology reacts to it. 


# How to Use

Unless you are writing code that is responsible for human lives, it can be hard to justify applying TVT at every decision. 

In my workflow, I usually write the prototype code first, staying very much aware of the fact that it IS a prototype, and that it's purpose is to be _changed_, maybe even _thrown away entirely_.

I then split the written code into Decisions. These are subjective, and I believe are best shown by example:

- our application has received some form of communication, we need to check whether the data inside the payload is correct and usable for our code, i.e. payload parsing / validation. 
- we need to find all items in our ecommerce shop that fit a certain condition, i.e. database access.
- we must mutate some data, filter it, emit it, or generate new data, i.e. processing.
- we must handle the different issues that can arise withing the codepaths, i.e. error handling.
- we must be able to understand what is going without performing live surgery on the running app, i.e. logging.
- we must be able give the user the ability to "do something", i..e. UI.

Think in terms of:

- Introducing a **new structure**, **assumption**, or **constraint**
- **Function signatures**
- **Data type definitions / transformations**
- Creating a **dependency** or **coupling**
- Encoding **invariants**, **transitions**, or **side effects**
- **Control flow decisions** (branching, recursion)
- **Resource boundaries** (IO, state, async, concurrency)
- **Interfacing with external systems** (APIs, DBs, queues)

After the decision have been defined, I start aggressively appling TVT, in order of appearance of the decision within the flow of the code/data. 

# Why does it work for me?

1. I am slowing down. 

My personal brand of the tism dictates that I move to writing the code as faster than I would like to, before having a clear picture in my head. 
Slowing down lets me take a more involved look at the design of the solution, find bugs, question my approach. To have a dialogue with the code.

2. I am giving shape to my thought. 

Inspired by psychology: we need to talk about the problem in order to give it a grounding in the real world via words and symbols. 
Transforming a void into a manageable and recognizable shape makes analysis possible.

3. I am my own reviewer.

I assume that there are problems, and, naturally, I find them and remove them.


# Sources

"Data-Oriented Design: software engineering for limited resources and short schedules" - Richard Fabian
