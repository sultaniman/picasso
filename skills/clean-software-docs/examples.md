# Clean Software Documentation — Examples

Examples drawn from William Zinsser, _On Writing Well_ (25th anniversary
edition, 2001), chapters on Clutter, Business Writing, and Usage. The targets
are corporate, governmental, and academic — but the failure modes are identical
to those in software docs and READMEs.

---

## 1. The corporate "customer bulletin" — a textbook of what to delete

A bulletin Zinsser quotes from a major corporation. Its purpose was to give
helpful information to a customer:

> Companies are increasingly turning to capacity planning techniques to
> determine when future processing loads will exceed processing capabilities.
> Capacity planning adds objectivity to the decision-making process. Management
> is given enhanced decision participation in key areas of information system
> resources.

Zinsser's translations:

- Sentence 1 → "It helps to know when you're giving your computer more than it
  can handle."
- Sentence 2 → "You should know the facts before you decide."
- Sentence 3 → "The more you know about your system, the better it will work."

**What it shows.** Three sentences, no people, no verbs of action, no specifics.
Every noun is abstract: _capabilities, objectivity, decision-making process,
decision participation_. Replace abstract nouns with concrete things people do,
and the prose comes alive.

**Software equivalent:** "This module facilitates the orchestration of data
ingestion workflows across heterogeneous source systems" → "Reads CSV and JSON
files into Postgres."

---

## 2. Corporate euphemism — saying the opposite of what you mean

Zinsser's list of real corporate phrasings:

| Said                                                                    | Meant                     |
| ----------------------------------------------------------------------- | ------------------------- |
| "Involuntary methodologies" (Digital Equipment Corporation)             | Laid off 3,000 people     |
| "Volume-related production-schedule adjustment" (General Motors)        | Plant shutdown            |
| "Negative cash-flow position"                                           | Went bankrupt             |
| "The aircraft should experience such an eventuality" (flight attendant) | The plane runs out of air |
| "Impacted with the ground prematurely" (Air Force)                      | A missile crashed         |

**What it shows.** Inflation hides accountability. The reader recognizes it
immediately and trusts the writer less for it.

**Software equivalent:** "Service degradation event" → "Outage." "Suboptimal
latency observed" → "Slow." "Customer-impacting incident" → "Users couldn't log
in for 40 minutes."

---

## 3. The same letter, written two ways (school principals to parents)

Zinsser analyzed letters from two real elementary school principals. Same
audience, same purpose, opposite results.

**Dr. Jones, Principal A:**

> Dear Parent: We have established a special phone communication system to
> provide additional opportunities for parent input. During this year we will
> give added emphasis to the goal of communication and utilize a variety of
> means to accomplish this goal. Your inputs, from the unique position as a
> parent, will help us to plan and implement an educational plan that meets the
> needs of your child. An open dialogue, feedback and sharing of information
> between parents and teachers will enable us to work with your child in the
> most effective manner.

**Dr. Dawson, Principal B (second paragraph of a "Principal's Greeting"):**

> Keep informed about what is planned for our children this year and let us know
> about your own questions and about any special needs your child may have. I
> have met many of you in the first few weeks. Please continue to stop in to
> introduce yourself or to talk about Foster. I look forward to a very
> productive year for all of us.

Zinsser's note: Dr. Jones is "clearly a man who means well, and his plan is one
we all want: to pick up the phone and tell the principal what a great kid Johnny
is despite that unfortunate incident in the playground last Tuesday." But Dr.
Jones doesn't sound like a person you'd want to call. Dr. Dawson does. Same
school, same purpose, completely different effect.

**What it shows.** When the writer reaches for institutional vocabulary —
"special phone communication system," "open dialogue, feedback and sharing of
information" — the reader stops trusting the message. Plain verbs and the first
person (_"I have met"_, _"Keep informed"_, _"Please continue to stop in"_)
rebuild that trust instantly.

**Software equivalent.** Compare:

> The package facilitates the implementation of stateful session management
> capabilities for distributed architectures.

with:

> Stores session data in Redis. Use it when your app runs on more than one
> server.

Same library. Only one of them gets used.

---

## 4. Clutter at the word level — what to bracket and cut

Zinsser's standing instruction to his Yale students: bracket every word doing no
work. After a term of doing this, most students could cut their first drafts by
50% with no loss of meaning. The most common offenders:

| Cut                                               | Replace with               |
| ------------------------------------------------- | -------------------------- |
| "Assistance"                                      | "help"                     |
| "Numerous"                                        | "many"                     |
| "Facilitate"                                      | "ease"                     |
| "Individual" (as noun)                            | "man" / "woman" / "person" |
| "Remainder"                                       | "rest"                     |
| "Initial"                                         | "first"                    |
| "Implement"                                       | "do"                       |
| "Sufficient"                                      | "enough"                   |
| "Attempt"                                         | "try"                      |
| "Referred to as"                                  | "called"                   |
| "At this point in time"                           | "now"                      |
| "Due to the fact that"                            | "because"                  |
| "In order to"                                     | "to"                       |
| "For the purpose of"                              | "for"                      |
| "Until such time as"                              | "until"                    |
| "With the possible exception of"                  | "except"                   |
| "It is interesting to note that"                  | (delete)                   |
| "It should be pointed out that"                   | (delete)                   |
| "I might add"                                     | (delete)                   |
| "Personally"                                      | (delete)                   |
| "Currently" / "presently" / "at the present time" | "now" or (delete)          |

The clutter words "up" and "free up" in _up_ and _free up_ shouldn't be there.
_Head up a committee_ → _head a committee_. _Face up to a problem_ → _face a
problem_. Examine every preposition appended to a verb.

**What it shows.** A README that uses _utilize_, _implement_, _leverage_, and
_facilitate_ once each is forgivable. A README that uses all four in one
paragraph is performing seriousness instead of conveying information.

---

## 5. Replace concept nouns with people doing things

Zinsser's three "dead sentences":

> The common reaction is incredulous laughter. Bemused cynicism isn't the only
> response to the old system. The current campus hostility is a symptom of the
> change.

Turned alive:

> Most people just laugh with disbelief. Some people respond to the old system
> by turning cynical; others say… It's easy to notice the change — you can see
> how angry all the students are.

**What it shows.** "There were no working verbs and no people. All the meaning
was buried in cold abstract nouns: _reaction, cynicism, response, hostility_."
Find the person, find the verb, and the sentence breathes again.

**Software equivalent.**

| Concept-noun version                                             | Person-and-verb version                                        |
| ---------------------------------------------------------------- | -------------------------------------------------------------- |
| "Error handling is implemented at the boundary layer."           | "The HTTP handler catches errors and returns 500."             |
| "Authentication occurs prior to authorization."                  | "The middleware checks the token before checking permissions." |
| "Configuration management is handled via environment variables." | "Read config from environment variables."                      |

---

## 6. Creeping nounism

Zinsser collected a real specimen:

> Communication facilitation skills development intervention.

(A program to help students write better.)

**What it shows.** When four or five abstract nouns chain together, no person is
doing anything and no verb is in the sentence. The most common modern source of
this is product naming inside companies — "Data Quality Monitoring Pipeline
Enhancement Initiative." If a sentence has more nouns than verbs by a factor of
three, rewrite it around one of the verbs you'd actually use to describe the
thing in conversation.

---

## 7. Active vs. passive verbs

Zinsser's example:

> "Joe saw him." vs. "He was seen by Joe."

The first is short, precise, leaves no doubt who did what. The second is longer,
vaguer (_how often_ was he seen? once? daily?), and saps the reader's energy.

**Software equivalent.** Changelogs and incident postmortems are notorious for
this:

| Passive                                                               | Active                                   |
| --------------------------------------------------------------------- | ---------------------------------------- |
| "An outage was experienced by the auth service from 14:02–14:47 UTC." | "Auth was down from 14:02 to 14:47 UTC." |
| "Logging has been enhanced to capture request IDs."                   | "Each request now logs its ID."          |
| "Tests are required to be added before merging."                      | "Add tests before you merge."            |

Passive is acceptable when the actor is genuinely unknown ("The cache was
corrupted") or genuinely beside the point ("The migration is run on every
boot"). Default to active.

---

## 8. The "I" disappears, and so does the meaning

Zinsser's diagnosis of corporate writing:

> The way to warm up any institution is to locate the missing "I." Remember: "I"
> is the most interesting element in any story.

In the school-principal example above, the warm paragraph uses "I have met many
of you" and "I look forward to." The cold one uses no first person at all and
reads like a generated artifact.

**Software equivalent.** Internal team docs, incident reports, and design
rationales lose force when they erase the author. Compare:

> A decision was reached to defer the migration to Q3 based on capacity
> constraints.

with:

> We deferred the migration to Q3 — the platform team is already booked through
> June.

The second tells the reader who, why, and what changed. The first tells the
reader nothing they couldn't have guessed.

---

## 9. The credibility test

Zinsser's rule:

> Don't inflate an incident to make it more outlandish than it actually was. If
> the reader catches you in just one bogus statement that you are trying to pass
> off as true, everything you write thereafter will be suspect.

**Software equivalent.** "Battle-tested in production at massive scale" — by
whom? "10x faster than the alternative" — than which one, on what workload?
"Zero-config" — really, no env vars? One unfalsifiable claim contaminates the
rest of the document. Make every claim something the reader could verify in five
minutes, or don't make it.

---

## How to use these examples

When editing software docs, find the example matching your draft's symptom:

| If your draft…                                        | Look at example |
| ----------------------------------------------------- | --------------- |
| Sounds important but says nothing                     | 1               |
| Hides what's actually happening behind euphemism      | 2               |
| Reads like a generated artifact                       | 3, 8            |
| Is full of inflated synonyms                          | 4               |
| Has long noun chains instead of verbs                 | 5, 6            |
| Drains the reader's energy with passive constructions | 7               |
| Makes claims you can't prove                          | 9               |
