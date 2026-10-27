# Decisions

This file says where a decision is written, which choices need an answer, and how an alternative that was dropped stays dropped. [The standard](../STANDARD.md#what-easy-to-change-asks-for) says why every behavior is either decided or incidental.

## Where decisions are written

A decision is written in the specification, which is wherever the project already writes what it has decided, such as its issues. The specification states what a person or another system sees the product do, and what must never happen, each where it can be found again and with its reason. How each is carried out belongs to the code and the as-built reference, as [documents.md](documents.md) says. In an issue, the decision is what it says the product does or must never do, and the rest is discussion. A decision changes only by asking, and is never rewritten to match what was built, because then a defect would become a requirement. Code that disagrees with it is a defect or a question.

A decision is an answer to one question from whoever asked, or a request from them naming what to build or change. Silence is not one, nor a recommendation nobody accepted, because neither says what was chosen. An answer such as "you choose" leaves the behavior incidental. A decision taken during the work is written, with the question it answers, in the plan or in the message of the commit that carries it, until it reaches the specification. A test written for a decided behavior says where it is decided, so that a failing test says which decision it protects.

## What needs an answer

You choose incidental behavior without asking, such as how a decided behavior is worded, laid out and shown in each of its states, within the [usability rules](../GOOD-TO-USE.md). Three kinds of choice need an answer instead:

- adding something the product does that no decided behavior asks for, such as a screen, command, option, endpoint or stored field of its own, or a step a document tells its reader to follow;
- a choice whose reversal would need more than a change to the code, or that others outside the code rely on: the shape of stored data, an address or link, an interface another system or person calls, the word for one of the product's concepts;
- a safeguard of "Trustworthy", that is, a check or limit that keeps the product trustworthy: removing one, narrowing what it protects, or adding one nothing requires.

## What is not proposed again

Before proposing something, search where decisions are written, and the history, because they say what was tried and why it was dropped. An alternative worth not proposing again is written with its reason beside the rule or behavior it concerns: the specification of an export might say "The export is not paged, because the largest export measured is 4,000 rows".
