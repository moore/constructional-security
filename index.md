
# Constructional Security

It is time for a new approach to software engineering.

Technology has crossed a chasm and connectivity is the new norm.  We face new network adversaries who have shown great success at overcoming the barriers we have placed around our software.

Where some well-funded and disciplined defenders have kept attackers at bay; it is at an ever-increasing cost that is already prohibitive for many.
 
Programmers are responding by internalizing security into, instead of surrounding, their software. Where protecting is put on par with communicating, creating, and managing. From end to end encryption, to process sandboxing, security is becoming a first-class citizen rather than a after the fact addition.

Constructional Security is a formalization of the process of internalizing security into software which offers an affordable approach to protecting users and data.

In order to achieve Constructional Security software must:

1. Isolate security controls from business logic.
2. Explicitly state security objectives and assumptions.
3. Ensure no software subsystem has access to authority beyond it' needs.

## Security Matrix
|                   |Credential Theft |Insider Threat |RCE    |Logic Bug|Information Leak|Backdoor|Phishing|Social Engineering|
|---                |---              |---            |---    |---      |--              |--      |--      |--                |
|2fa                |YES              |NO             |NO     |NO       |NO              |NO      |YES     |NO?               |
|Encryption at Rest |NO               |Yes            |NO     |NO       |NO              |NO      |NO      |NO                |
|Memory Encryption  |NO               |NO             |NO     |NO       |NO              |NO      |NO      |NO                |
|Audit Logs         |Partial          |Partial        |Partial|NO       |NO              |NO      |YES     |YES               |
|Polymorphism       |NO               |NO             |YES    |NO       |YES?            |NO      |NO      |NO                |
|Formal Methods     |NO               |NO             |YES    |YES      |YES             |YES     |NO      |NO                |
|Object Capabilities|NO               |NO             |NO     |YES      |YES             |NO      |NO      |NO                |
|Safe Languages     |NO               |NO             |YES    |NO       |YES             |NO      |NO      |NO                |
|Sandboxing         |NO               |NO             |YES    |NO       |YES             |YES     |NO      |NO                |
|Role Separation    |Partial          |Partial        |NO     |NO       |NO              |NO      |YES     |YES               |
|E2e encryption     |YES              |YES            |NO     |YES      |YES             |YES     |YES     |NO                |

## Motivation


Bugs in functional parts of software can usually be worked around once they are encountered, but for safety concerns, a single failure is usually unacceptable.

## Goals

### Common Lexicon

Formal methods, object capabilities, APSEC, and other communities often use different terms to talk about ideas related to Constructional Security. If we had more understanding of each others languages we could better understand how each communities ideas can contribute.

### What are the proprieties Constructional Security

What approaches and practices are required for a some software to be said to have Constructional Security? It is an explicit goal that we define the term to be inclusive to many approaches to "built-in" security, formal methods, ocap, etc. My current thinking (july 4th 2020) is that that:

 - It must be possible to reason about the security a system. (but what dose this mean?)
 - The goal of any control must be explicitly stated.
 - Each control must be precisely specified.
 - Each control must have it's dependencies and assumptions explicitly stated.

 What dose this exclude? What dose it miss? Can it be simpler?

## Terminology

### Controls
A control is a mechanism which constrains the behavior of a system in order to maintain safety or policy requirements. 

## Topics

### Features Vs. Bugs
Each feature one adds to a code base will tend to increase the lines of code deployed; but defects scale linearly with lines of code and it is reasonable to assume the same goes for vulnerabilities. Our current approach to software engineering depends on large amounts of ambient authority leading to the unfortunate outcome that software becomes less secure the more useful it becomes.

As a result we believe we must rethink how software is developed to separate code which provides safety from code that is functional.

### Correctness and Weird Machines
For any safety critical code we should have a explicit goal of showing that only expected states can be reached though intended transitions. This model of thinking is based on the idea of Weird Machines (https://en.wikipedia.org/wiki/Weird_machine), which is a theory of exploitation. Under this theory all programs can be viewed as a state machine and an exploit is data which abuses unintended states and transitions in the state machine to overcome controls implemented in the software.

### Safety Engineering
In this document I refer to safety instead of security with the idea that security is a kind of safety. What can we learn from the safety engineering community?

