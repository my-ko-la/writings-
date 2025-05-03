
# Disclaimer 

This article is brought to you by organic, pure-bred thought and subjective rationality - no AI tools were used to articulate, edit, influence, or in any form interact with the contents of the article.

# Introduction 

Throughout my comparatively short programming career I have had the pleasure to experience how unlike any other discipline programming, or, perhaps more appropriately, software engineering [[EDIT: why is it more appopriate]] is different from any other activity I have attemped before.

It has the capacity to bring intense feelings of joy and satisfaction, not only from the problem solving, but from the struggle, the challenge, the growth. I have been pretty lucky to work with talented developers, from whom I have learned a lot. XX_random?

The discipline, however, is far from a tranquil walk in the park. It can drain you, mentally and emotionally. On numerous occasions I have experienced the exhaustion that comes from thinking about a problem for hours on end, only to discover the answer seemingly on a whim the next day (surprisingly, quite often while being in a room that has all the properties of a bathroom) [[EDIT: this joke can be made better]]. 

It makes you keenly aware of your shortcomings, whether they are in faulty reasoning, misunderstood requirements, a lack of education, unused systems thinking, interactions with time management - the list is long. 

You get better at recognizing these shortcomings, you get faster at overcoming them, to the point where they do not require active cognitive attention, and are essentially baked into your logic when designing and developing software. Yet, you still find yourself making errors, ranging from a simple "I left a typo in the log" oopsie to a production-breaking fucky-wucky.

## So, why the yapping?

With this article, I want to distill and, as neatly as is possible for me, formalize my findings and highlight my current approach to problem solving. I want to sprinkle some tidbits of knowledge and concepts that I find to be the most bang for your buck, so that you do not spend hours doing fuck all, rather than making the computer do work. XX_idea is great but I don't like the phrasing 

If at any point while reading you find yourself thinking that I am throwing some shade at common and popular programming concepts, you are not wrong. I have spent a not-insignificant amount of time wrestling with the framework, rather than contributing to the solution; and I want revenge.

As someone who is self-taught, I like to think that I have an outsider's perspective, and I am not beholder to the jaws of familiarity that for some have been closed since their uni years. 
My objective is to make devs consider a simpler approach. (And for recruiters to see that I, like, a good investment). 

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

In my workflow, I usually write the prototype code first, staying very much aware of the fact that it IS a prototype, and that it's purpose is to be _changed_, maybe even  _thrown away entirely_.

I then split the written code into Decisions. These are subjective, and I believe are best shown by example rather than via definition: 

- our application has received some form of communication, we need to check whether the data inside the payload is correct and usable for our code, i.e. payload parsing / validation. 

- we need to find all items in our ecommerce shop that fit a certain condition, i.e. database access.

- we must mutate some data, filter it, emit it, or generate new data, i.e. processing.

- we must handle the different issues that can arise withing the global codepath, i.e. error handling.

- we must be able to understand what is going without performing live surgery on the running app, i.e. logging.

- we must be able give the user the ability to "do something", i..e. UI.

Mix and match these and you get software. Mix and match software and you get systems. 

Things go out out control fast: the least we can do is to make sure that our code is CORRECT and RIGOROUS. 







# Sources

"Data-Oriented Design: software engineering for limited resources and short schedules" - Richard Fabian
