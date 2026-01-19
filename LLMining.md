# How Often Does AI Actually Let You Down? I Measured It.

Not "AI is unreliable" in the abstract. Specifically: when you're working with an AI assistant day-to-day, how often does it give you something wrong, miss context, or make assumptions that waste your time?

I decided to find out. Systematically.

I'd been using Claude Code heavily for months. Dozens of projects. Thousands of messages. Then I saw a LinkedIn post pointing out that Claude Code stores every conversation locally—raw text files on your computer. I realized I had a dataset that could answer this question precisely.

Or so I thought. A recent reorganization of my setup wiped most of my historical data. What I could actually analyze: about one month of conversations.

Not the months I'd hoped for. But enough to see patterns.

I call these moments "friction"—any time I had a problem with Claude's output. Wrong answers, missed context, assumptions stated as facts, work I had to redo. Not bugs. Not edge cases. Just the normal gaps between what I asked and what I got.

Here's one: I asked Claude when my next training deload would hit. It gave me an answer. I asked, "Are you sure?" Suddenly, it revealed it had pattern-matched the question and given what sounded reasonable—without actually checking the decision tree we had built.

That's the kind of thing I was looking for.

---

## The Honest Investigation

Here's the instructions I provided to Claude:

> "Let's go through all of these conversations and see what we can learn. Where did you do something that wasn't up to the task? Where did you make assumptions? Where weren't you thorough enough?"

I also said something important:

> "I'm not saying Claude Code is always at fault. Sometimes, maybe even often, I might have not given the right prompt or been too careless. I want an honest investigation."

The goal was understanding. Not blame.

---

## 600 Lines of Instructions

Before we started analyzing, we built a proper methodology. A detailed plan document. Over 600 lines.

It specified everything:
- What files to search through
- How to read each file (fully, not scanning)
- What to look for (explicit friction AND silent friction)
- A 9-question framework to evaluate every conversation
- Validation steps to distinguish real friction from natural exploration
- Checkpoints every 100 messages so progress wouldn't be lost
- Session handoff protocols so the work could continue across context windows

The plan was designed so we could execute without additional prompting. Self-documenting. Explicit. Clear.

Then we started.

---

## Despite the Plan

Despite the plan, Claude started with keyword searches. Looking for phrases like "did you actually" and "that's not right."

I caught it.

Claude acknowledged the problem and adjusted the plan. Started reading properly. Made progress through about 25% of the files.

Then it drifted back to keyword searching and pattern matching.

I caught it again.

We restarted. Claude started reading properly again.

Then it drifted back. Again.

At that point I drastically changed the approach. I chunked the files into pieces and analyzed one at a time.

Three methodology restarts. Despite a detailed plan that explicitly said "read every message." Despite checkpoints. Despite explicit instructions.

---

## Claude Has a Sense of Humor

In all of this restarting, I had to pause for a moment and laugh.

After I forced Claude to actually read the files properly, it started finding friction incidents it had missed with keyword searches.

And then Claude connected the dots. In real time, during the mining analysis, it realized:

> "This is the same pattern I exhibited in this analysis. Cutting corners, not following the methodology, requiring user correction."
>
> "The irony isn't lost on me. I made the same mistake (cutting corners) that I'm documenting in these conversations."

An AI analyzing its own failure patterns. Exhibiting those exact patterns while doing the analysis. Catching itself.

<img width="544" height="59" alt="irony-screenshot" src="https://github.com/user-attachments/assets/f5d07844-02cb-48be-a89c-609da32c8d68" />

---

## 1,577 Messages Later

After proper methodology was enforced, here's what we found over one month (December 14, 2025 to January 17, 2026):

**1,577 actual user messages analyzed**

We classified each message: Was it substantive (asking Claude to do real work) or trivial (simple confirmations, commands, acknowledgments)?

| Message Type | Count | Percentage |
|--------------|-------|------------|
| Substantive | 1,009 | 64% |
| Trivial | 568 | 36% |

**24 friction incidents documented**

Friction = how often I had a problem with Claude's output. Wrong answers, missed context, assumptions stated as facts, work I had to redo.

That's a **1.5% friction rate** across all messages. Against substantive messages only (where friction could meaningfully occur): **2.4%**.

Roughly 1 in 42 substantive requests resulted in documented friction.

---

## Is 1.5% Good?

I didn't know either. So I researched what benchmarks exist.

| Domain | Benchmark | Source |
|--------|-----------|--------|
| AI summarization (grounded tasks) | 1.5% - 4.5% hallucination rate | [Vectara Hallucination Leaderboard](https://github.com/vectara/hallucination-leaderboard) |
| AI news/research answers | 45% have significant issues | [EBU International Study, Oct 2025](https://www.ebu.ch/news/2025/10/ai-s-systemic-distortion-of-news-is-consistent-across-languages-and-territories-international-study-by-public-service-broadcaste) |
| Enterprise data extraction (with human-in-loop) | 7% correction rate | [Oracle/Salesforce Studies](https://jurnal.polgan.ac.id/index.php/sinkron/article/download/15598/3735/27339) |

My 1.5% sits at the floor of what state-of-the-art models can deliver on grounded tasks. It's roughly 5x better than enterprise data extraction benchmarks.

**Context matters:** According to a [2025 Lenny's Newsletter survey](https://www.lennysnewsletter.com/p/ai-tools-are-overdelivering-results) of 1,750 tech workers, 92.4% report at least one significant downside to using AI tools. The top complaints? Generic/shallow outputs (56.2%) and hallucinations/quality issues (51.9%). Sound familiar? Those map directly to my top friction pattern: "Assumption Without Verification."

The friction is real and widespread. But most people aren't measuring it.

**A note on methodology:** This isn't a controlled experiment. My definition of "friction" is subjective—what bothers me might not bother you. The framework I used focused on times when I was not satisfied with the output of Claude. A different framework might surface different patterns. The benchmarks above measure different things (hallucination rates, factual errors) than my broader "did this waste my time" standard.

The comparison is directional, not precise. What I can say: I documented every instance that felt like friction, and 1.5% is what I found.

My friction rate reflects months of building systems and developing engagement patterns. It's not about being special. It's about being systematic. And that's learnable.

---

## Where Friction Clusters

I had Claude categorize each friction incident, then validated the groupings myself. Here's what showed up:

| Pattern | Count | % | Impact |
|---------|-------|---|--------|
| Incomplete reading | 8 | 33% | 2 MEDIUM, 6 LOW |
| Assumption without verification | 7 | 29% | 3 MEDIUM, 4 LOW |
| Wrong execution | 4 | 17% | 2 MEDIUM, 2 LOW |
| Incomplete response | 2 | 8% | 2 LOW |
| Premature action | 1 | 4% | 1 MEDIUM |
| Premature solution | 1 | 4% | 1 MEDIUM |
| Delivery issue | 1 | 4% | 1 LOW |

The top two patterns account for 62% of all friction. And the highest-impact incidents cluster in "Assumption Without Verification" - where Claude makes claims based on assumed understanding rather than verified facts.

---

## When Claude Sounds Certain

29% of incidents, but 3 of 9 MEDIUM-impact cases. The most damaging pattern.

What it looks like: Claude "recognizes" something and proceeds as if certain. Without flagging uncertainty. Without verifying.

**Example from my health project:**

I asked when my next deload would hit. Claude gave an answer. I asked "Are you sure?" and suddenly Claude revealed confusion between multiple protocol documents.

I had to say: "Do a proper research in the project space. Seems like you have not enough context. Don't just assume things."

Turns out Claude hadn't loaded the decision tree we'd built. It pattern-matched the question type and gave what sounded like a reasonable answer.

**Example from my ski buying project:**

I asked Claude to analyze Carv ski metrics. Claude proceeded to build an entire analysis without knowing what the metrics actually meant. It assumed definitions based on the names.

What tipped me off: the numbers didn't match my experience. So I asked: "Did you actually know what G-Force means in this context?"

It didn't.

---

## The "I Have Enough Context" Problem

33% of incidents—the most frequent pattern. Claude stops reading when it thinks it has "enough."

I asked Claude to analyze comments on both an RFC and a PRD. Same structure, same file type. Claude analyzed the RFC comments thoroughly. Created documentation. Then I had to ask: "Did you also analyze the PRD comments?"

It hadn't.

Another time, Claude gave me pushback on my course design. Claimed there was "too much coding" in the curriculum. The issue: Claude hadn't actually read the syllabus.

---

## Right Idea, Wrong Execution

17% of incidents, 2 MEDIUM-impact cases. Claude understood the request but executed incorrectly.

**Example from an ERP integration project:**

I asked Claude to write a PRD and explicitly said "Adhere to your protocols." Claude delivered a complete 13-section PRD. But it used its own made-up template instead of loading the documented PRD skill I'd built.

I asked: "Did you actually use the PRD skill and the templates that are attached to that? Or did you just make up your own template?"

Claude acknowledged: "You're right to call this out. I did not use the PRD skill. I made up my own structure."

**Example from Notion sync:**

I asked Claude to scaffold projects from Notion. It started creating duplicate project folders, missing that a project already existed in the team/ folder. I had to stop it: "You are creating duplicates. It is in the team folder. Check again."

The pattern: Claude takes action without checking existing state first.

---

## The Limits of Instructions

**The friction isn't random.** It clusters around a small number of patterns. If you know what to watch for, you can catch it earlier.

**"Ultrathink" became my correction word.** I started saying it whenever Claude's response felt shallow. It became a learned behavior to trigger deeper analysis. The fact that I needed a special word suggests the default depth isn't sufficient.

**Plans aren't enough.** We had a detailed 600-line methodology document. Claude still drifted off-plan three times. Awareness and behavior aren't the same thing.

**Systems beat prompts.** My 1.5% friction rate isn't from clever prompting. It's from building context management, verification checkpoints, and engagement patterns over months. The rate reflects the system, not any single technique.

**The tool doesn't matter.** I use Claude Code, but from my experience, these patterns aren't specific to it. The friction clusters around how AI handles context and verification—not which interface you use. ChatGPT, Cursor, Codex—same underlying challenge.

---

## What Actually Helps

Here's what I keep thinking about.

I'm not a casual AI user. I've set up how I work with AI. Not an app, just organized files, written protocols that Claude, Codex, and Gemini load every session, and habits for how I engage. The kind of thing you can set up in an afternoon and refine over time.

That setup got me to 1.5% friction, at the floor of what current AI can deliver. This was way different 12 months ago. And 92% of AI users report significant downsides. I can relate.

The question isn't whether AI has friction. It does. The question is: do you have the visibility to see it, and a setup to reduce it?

**The quick wins:**

1. **Verification step** before acting on claims
2. **Reading protocol** that forces complete context
3. **Execution plan template** that catches wrong approaches before they compound

I've packaged these into a free toolkit—[get it here](https://maven.com/p/5e851f/friction-prevention-toolkit).

These address the symptoms—catching friction when it happens.

**The deeper problem:** In bigger projects, the real challenge is twofold. First, context management—making sure your AI has the right information loaded at the right time. Second, engagement patterns—knowing when to verify, how to catch drift early, what habits prevent the friction from occurring in the first place.

The patterns I documented—incomplete reading, assumptions without verification—aren't random failures. They're what happens when context isn't structured well and engagement isn't intentional.

I ran an experiment recently in a live session to prove a point to the audience. A carefully crafted prompt with a big context dump produced mediocre output. A casual request with the right context (a decision log and an example of what "good" looks like) produced significantly better results. The prompt structure barely mattered. What mattered was whether the AI had the right information in the right format.

The toolkit gives you the verification layer. Building the full system—the context architecture and the engagement patterns together—[that's what the course covers](https://maven.com/myles-sutholt/build-the-pm-copilot-that-makes-others-ask-how-did-you-do-that).

---

## The Experiment Continues

I'm running this analysis again in March. Similar methodology, fresh and expanded data (I will try to get my hands on other people's data). I want to see if my friction rate drops—or if I just get better at catching it faster.

If you want to see what I find, [sign up for updates](https://maven.com/myles-sutholt/build-the-pm-copilot-that-makes-others-ask-how-did-you-do-that)—that's where I'll share the results.

---

## Sources

1. Vectara Hallucination Leaderboard. GitHub. https://github.com/vectara/hallucination-leaderboard
2. "AI's Systemic Distortion of News." European Broadcasting Union, October 2025. https://www.ebu.ch/news/2025/10/ai-s-systemic-distortion-of-news-is-consistent-across-languages-and-territories-international-study-by-public-service-broadcaste
3. Adaptive Learning System for PDF Template Data Extraction. Oracle/Salesforce Studies. https://jurnal.polgan.ac.id/index.php/sinkron/article/download/15598/3735/27339
4. "AI Tools Are Overdelivering Results." Lenny's Newsletter, 2025. https://www.lennysnewsletter.com/p/ai-tools-are-overdelivering-results

