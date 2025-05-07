
# Disclaimer 

This article is brought to you by organic, pure-bred thought and subjective rationality - no AI tools were used to articulate, edit, influence, or in any form interact with the contents of the article. I think AI can be used in cool ways, even productive ones - but _I_ like writing, so _I_ will write. 

# Why the yapping?

Programming isn’t like any other craft — it thrives on struggle as much as insight. You prototype fast, hit dead-ends, then wake up with solutions.

I have seen many different ways of solving the same problem, and have started to _form opinions_. 
I want to share some of these _opinions_, ones I find can be useful for you, as they were for me.

I am not pretending to have introduced a Revolutionary New Paradigm, what you will read below is embarrasingly self-evident.

## Before we dive in

I want to mention that I plan to tackle other topics that I hold close to heart in the next posts. Let me know what you think of the names: 

- "Embracing Data-Oriented Design, cache lines and how to love and cherish the CPU."
- "Does the code itself need DDD?"

# How I tackle problems: Trace-Validate-Test

Within this article, I want to distill and, as neatly as is possible for me, externalize my thoughts and share my current approach to problem solving. 

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

- Is it necessary, or just familiar?
    
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

In my workflow, I usually write the prototype code first, staying very much aware of the fact that it IS a prototype, and that its purpose is to be _changed_, even _thrown away entirely_.

I then split the written code into Decisions. These are subjective, and I believe are best shown by example:

- our application has received some form of communication, we need to check whether the data inside the payload is correct and usable for our code, i.e. payload parsing / validation. 
- we need to find all items in our ecommerce shop that fit a certain condition, i.e. database access.
- we must mutate some data, filter it, emit it, or generate new data, i.e. processing.
- we must handle the different issues that can arise within the codepaths, i.e. error handling.
- we must be able to understand what is going without performing live surgery on the running app, i.e. logging.
- we must be able give the user the ability to "do something", i.e. UI.

Think in terms of:

- Introducing a **new structure**, **assumption**, or **constraint**
- **Function signatures**
- **Data type definitions / transformations**
- Creating a **dependency** or **coupling**
- Encoding **invariants**, **transitions**, or **side effects**
- **Control flow decisions** (branching, recursion)
- **Resource boundaries** (IO, state, async, concurrency)
- **Interfacing with external systems** (APIs, DBs, queues)

After the decision have been defined, I start aggressively applying TVT, in order of appearance of the decision within the flow of the code/data. 

# Example use case

todo()!
- something NestJS-y 
- db, validation, types, invariant holding...

# Why does it work for me?

1. I am slowing down. I tend to rush to code before I’ve thought things through, before having a clear picture in my head. Slowing down lets me take a more involved look at the design of the solution, find bugs, question my approach. To have a dialogue with the code.

2. I am giving shape to my thought. Inspired by psychology: we need to talk about the problem in order to give it a grounding in the real world via words and symbols.Transforming abstract thoughts into a manageable and recognizable shape makes analysis possible.

3. I am my own reviewer. I assume that there are problems, and, naturally, I find them and remove them.

4. I am getting more confident about the code, and am improving the rigor required to guarantee correct execution.

# Closing words

If you're still with me then thanks for taking the time to read the above. As a farewell gift, allow me to show you how TVT can be expanded to cover not only code: 

## SYSTEM DESIGN

### TRACE
- What user or business needs drove this?
- What implicit constraints shape it? (SLA, cost, failures)
- What real-world process does it abstract?

### VALIDATE
- Are responsibilities correctly bounded?
- Are invariants enforced? Where?
- Is the scope minimal or conflated?

### TEST
- What couplings does this introduce?
- What failure modes emerge (runtime/scale/deploy)?
- How does this shape the evolution of the system?

---

## TYPE / DATA DESIGN

### TRACE
- What domain concept is modeled?
- What abstraction level is this? (semantic/structural/protocol)
- Is it for logical clarity or implementation convenience?

### VALIDATE
- Does it prevent illegal states?
- Are all invariants encoded?
- Is it the minimally viable structure?

### TEST
- Who depends on this type now?
- What versioning/migration pain is created?
- How extensible is it without leaking abstraction?

---

## ALGORITHM SELECTION

### TRACE
- What are the input size, shape, and characteristics?
- Is this problem exact, approximate, or heuristic?
- What prior patterns does it resemble?

### VALIDATE
- Is the algorithm optimal for the intended input profile?
- Are time/space/resource bounds provable?
- Are hidden assumptions safe?

### TEST
- How does it integrate with surrounding layers?
- What does failure look like?
- What tradeoffs am I hardcoding in?

