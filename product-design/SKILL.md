---
name: product-design
description: Shape a product's model before its screens - users and jobs, objects and relationships, main workflow, information architecture, navigation logic, progressive disclosure from first-time to expert and from one person to an organisation - for any product type or platform.
---

# Product design

Turn what the product can really do into a coherent model before arranging any screen. The result should work
for a first-time user and an expert, for one person and a large organisation, without becoming two products.
This applies to any product: a mobile app, a website, a desktop tool, a command line, a service with an API,
a device.

## 1. Gather evidence

- what the product is for and who it is for, as currently decided;
- what it can actually do today, from the real implementation, and what is only planned;
- the terms it already uses in its interface and its translations;
- which surfaces exist or are planned, and what each is for;
- product decisions already made and accepted. Refine those; do not reopen them without a new reason.

Do not infer a capability from a mock-up, an old roadmap or an attractive component.

Done when capabilities are listed as existing or planned, with the source of each.

## 2. Population matrix

Cover the combinations that apply to this product:

| Dimension | Range |
|---|---|
| Experience | first use, occasional, expert |
| Organisation | one person, a team, a regulated organisation |
| Scale | one item, many, a very large history |
| Autonomy | the person does it, the product assists, the product acts under supervision |
| Environment | online, slow, offline, reconnecting |
| Device and platform | each form factor and operating system the product ships on |
| Language | each shipped language, with room for longer text |

Progressive disclosure may change density and shortcuts. It never hides who is allowed to do something, what
it costs, what the risk is or what cannot be undone.

## 3. Model the product

1. State the user's job and the decision the interface must support.
2. Identify the real objects and how they relate. Use the system's actual structure, not a tidy diagram that
   the product does not follow.
3. Map entry, success, failure, interruption, recovery and return.
4. Model the main workflow first, end to end: from the person's intent, through the action, to seeing the
   result and trusting it.
5. Separate four kinds of thing: doing, inspecting, explaining and configuring.
6. Decide what belongs on each surface. A surface that only shows information must not become a second place
   to give commands.
7. Define how complexity grows for the expert and the organisation without duplicating the model.
8. Check every noun and action against the real product and its translations.

Done when the main workflow and its failure paths can be walked on paper without an invented state.

## 4. Information architecture rules

- Organise around what the person intends and what state things are in, not around the code's module names.
- An action and its result stay traceable as one chain.
- What is true now, what is wanted and what happened before are distinct in both words and appearance.
- The primary action is unambiguous; a dangerous action shows what it affects and what follows.
- An empty state teaches a valid next step without inventing sample activity.
- Long lists get search, filter, grouping, saved views and stable links where the product supports them.
- One name per thing, everywhere.

## Output

A short product contract:

- users and their jobs;
- the object and relationship model;
- the main workflow and its critical variants;
- what goes on which surface;
- navigation and progressive-disclosure logic;
- permission, empty, stale, loading, failure and recovery states;
- open questions that the product's owner must decide;
- the evidence that will show it works, tied to real capabilities.

Do not move to visual polish while the model still has contradictory ownership or invented states.
