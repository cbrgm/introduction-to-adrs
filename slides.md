# An introduction to Architecture Decision Records

👨‍💻 __Christian Bargmann (Github: cbrgm)__

🐦 @chrisbargmann

📧 chris@cbrgm.net

---

## What are we going to cover?

Today we will talk about

* what Architecture Decision Records are
* how ADRs deliver value to your team

we will also do a short practice (in small groups) to learn

* how to create ADRs

---

## Why ADRs? Let's imagine the following conversation

```
Dev1: Yo, I can't run our integration tests locally anymore

Dev2: Yeah, we decided to switch to Consumer Driven Contract Tests provided by
Team Route-Navigation so you'd have to run the service on our dev cluster

Dev1: Uh, when did we decide that?

...

```
---

## What do we need to solve?

> We need to make decisions to move forward.

> We can't move forward unless everyone understands our decision.

---

## Can't we just verbally communicate changes?

Conversations are great to share design decisions especially while we're exploring the architecture (for example in pairing mode)

But oral history has limits:

* Short reach (we can't talk to everyone at once)
* Changes organically ("Stille Post")
* Time consuming to share
* Dies without constant attention

---

## What other options do we have to share decisions?

* Code Comments?
* Wikis like Confluence, ... ?
* Documents?
* Emails, Slack Messages?

Also we need a format, a structure how to capture the "right" thing

---

## Architecture Decision Records

Let's start with `A` = Architecture. Remember Software Engineering from your Bachelor courses?

> The basic organization of a system, represented by its components, their relationships to each other and to the environment, and the principles that govern the design and evolution of the system.

---

## Architecture Decision Records

In other words: A software architecture is a set of significant design decisions.

---

## Architecture Decision Records

What about the `D`? Decisions modify

> The basic organization of a system, represented by its components, their relationships to each other and to the environment, and the principles that govern the design and evolution of the system.

---

## Architecture Decision Records

They strongly influence...

* Structure (for example, patterns such as microservices)
* Non-functional requirements (security, high availability, and fault tolerance)
* Dependencies (coupling of components)
* Interfaces (APIs and published contracts)
* Construction techniques (libraries, frameworks, tools, and processes)

Decisions can be somewhere in between of being extremely costly to go back and easy to change your mind.

---

## Architecture Decision Records

What is a "significant decision"?

* Because of `decision`, component X will be more difficult to test
* Because of `decision`, component X now depends on a third-party library not actively maintained
* Because of `decision`, the code of component X will move to new packages / modules
* Because of `decision`, we accept technical dept but we will ship faster.
* Because of `decision`, all devs will need the cli tool `x`
* Because of `decision`, the config file gets two new parameters

---

## Architecture Decision Records

And finally, let's talk about the `R`!

> An architectural decision record (ADR) is a document that describes a choice the team makes about a significant aspect of the software architecture they’re planning to build.

---

## Architecture Decision Records

An ADR should contain the following:

* A Context
* A Decision
* A list of Consequences

ADRs have states (accepted, proposed, ...) and therefore follow a lifecycle.

---

## ADR: Use a template

```
Title: A title for a decision to be made

Date: 2022-11-05, Author: Christian Bargmann ([@cbrgm <chris@cbrgm.net>](mailto:chris@cbrgm.net))

## Status

- [x] - Proposed

## Context

What is the issue that we're seeing that is motivating this decision or change?

## Decision

What is the change that we're proposing and/or doing?

## Consequences

What becomes easier or more difficult to do because of this change?

```

---

## ADR: How to structure them?

Example:

```
.
├── README.md
├── docs
│   └── decisions
│       └── 001-example-adr.md
├── slides.html
├── slides.md
└── ...
```

---

## ADR: Examples

[Let's look at some ADR examples :)](https://github.com/adr/madr/tree/main/docs/decisions)

---

## Architecture Decision Records

A collection of multiple ADRs creates a `Decision Log`.

>  The decision log provides the project context as well as detailed implementation and design information.

> Project members skim the headlines of each ADR to get an overview of the project context. They read the ADRs to dive deep into project implementations and design choices.

---

## Architecture Decision Records

* When the team accepts an ADR, it becomes immutable.
* If new insights require a different decision, the team proposes a new ADR.

---

## Tips: Consider the following when writing ADRs

* Use plain, direct language
* Make in short: 1-2 pages max
* Personal preference: Markdown
* Store ADRs alongside with your code e.g. `./docs/adrs`

---

## Benefits of ADRs

* Easy to edit, easy to find
* Plain text works great, doesnt need pictures
* Easy to consume and change by your colleagues
* Low entry-barrier for your team members
* Easy to ramp up over time

---

## Tips: Tooling

* MADR - Markdown Architectural Decision Records
* Michael Nygard's template - The first incarnation of the term "ADR". Maintainable by adr-tools.
* Sustainable Architectural Decisions - The Y-Statements
* DecisionRecord - Agile records by Mathias Schubanz
* Other templates listed at https://github.com/joelparkerhenderson/architecture_decision_record

---

# Let's do some practice!

---

## Today's mission

* Work in pairs or small groups
* [https://github.com/PokeAPI/pokeapi](https://github.com/PokeAPI/pokeapi)
* Let's design a public API for the new Pokemon Generation Scarlet and Violet (release in two weeks).
	* Multiple clients (Web Clients, Android/iOS App, SmartHome Assistant)
	* Image Sprites + Description is provided
	* Multiple languages supported

---

# Your task: Create a decision record for your design

---

## Before we start

* No right or wrong answers
* Watch the clock
* Ask me questions if you need help
* Fill in project gaps with your imagination (or ask)

---

## A simple example

```
Title: Use GraphQL for client communication

Context:

We need to support multiple devices simultaneously. We also have to save
bandwith by reducing the number of network round trips to our backend infrastructure.

Decision:

We decided to use GraphQL for client communication. GraphQL lets you ask
for what you want in a single query, saving bandwidth and reducing waterfall requests.
It also enables clients to request their own unique data specifications.

Consequences:

For example, in an application that uses a few fields the same way each time,
using GraphQL adds more complexity because of things like types, queries, mutators, resolvers,
and higher-order components, From a maintenance perspective, this is especially detrimental.

```

---

# Meet your team! (5 minutes)

* Self organize into pairs or small groups

---

# Sketch a high-level design for our Pokemon API (7 min)

* Sketch a picture or two
* Context diagrams are great
* Lean on your experience, feel free to add buzzwords (Kubernetes, AWS, IoT, Blockchain)

---

# Make a decision (5 min)

* Use imperative voice: "We will..."
* Make sure it's architectural, for example adding unit tests is not an architectural decision
* Keep it brief, say it in one sentence

---

# Describe the context (7 min)

* What experts are influencing the decision?
* State the context as "given" / as a fact
* Again, keep it brief

---

# Outline the consequences (7 min)

* Consequences can be either good or bad
* Start with something like "As a result, ..."
* Are there risks alongside with your decision?
* Be a little bit more precise than "the system becomes more complex".

---

# Now, present your ADR to another group (12 min)

* What was the decision?
* Does the decision make sense for the given context?
* Can you think of more consequences?

# Let's wrap it up!

---

## Let's wrap it up!

Today we talked about...

* ...what Architecture Decision Records are
* ...how ADRs deliver value to your team
* ...how to create ADRs

---

## Final words

* Foster a documentation habit
	* Get the whole team involved
	* Spread knowledge
* Do Peer Reviews on ADRs or pair while writing them
* Do you have a dedicated Architect? Let him point out when to write an ADR
* Track ADRs in the backlog / create a story for them
* Not everything is an ADR, continue drawing pictures and diagrams and capture other views on your system

---

## Literature

* Architecture in Practice by Len Bass, Paul Clements, Rick Kazman (1997)
* Documenting Software Architecture by Paul Clements (2002)
* A documentation framework for Architecture Decisions by Uwe Van Heesch et al. (2011)
* Documenting Architecture Decisions by Michael Nygard (2011)
* [https://adr.github.io/](https://adr.github.io/)
* [https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/adr-process.html](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/adr-process.html)

---

# Thank you!

👨‍💻 __Christian Bargmann (cbrgm)__

🐦 @chrisbargmann

📧 chris@cbrgm.net

