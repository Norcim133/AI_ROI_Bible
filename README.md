# AI_ROI — the Enthoosa approach

**tl;dr:** the ROI of AI is found by counting. Count the items going into a process and the items coming out (support calls, board papers, onboarded clients), before and after AI, and convert the change in those counts into either a) FTE you no longer need or b) lead time you no longer wait, which is revenue you earn earlier. Everything in this repo is a way of doing that counting well. If you use the material, please call it the "Enthoosa approach" and link here (Thoosa was the Greek goddess of swift currents).

The README is built to be skimmed. Each section stands alone.

## Try it in ten minutes

Pick one process where AI has been deployed, or is about to be: claims processing, support handling, pen testing, vendor contracting, or project delivery are all good examples. Any process you know well at your level in the org is fine.

Get four numbers from the month before the AI went in, and again for the month after. If it hasn't gone in yet, the "before" is your baseline and you come back for the "after."

The four starting numbers you need:
1. **Demand**: items that arrived in the month.
2. **Completions**: items finished in the month.
3. **Open Items**: items open at month end.
4. **FTE**: people working the process.

Note that you don't need these in an Excel or as output from a data pipeline. Just get the 4 numbers.

The two numbers you derive:
1. **Lead Time**: the time it takes for a work item to transit across your org (Open Items ÷ Completions)
2. **Completions per FTE**: the amount of items per month a given FTE can deliver (Completions ÷ FTE)

Now compare before and after. There are three possible outcomes.

- **Completions per FTE rose, but Completions already matched Demand.** Here the ROI comes from a reduction in direct cost. You can calculate this by taking the incremental increase in Completions ÷ Completions per FTE. This tells you how many FTE's worth of capacity AI is now delivering and, by extension, how many FTE you can release.
- **Completions per FTE rose, and Completions started below Demand.** The AI is clearing a queue at a constraint. Once the queue is down, you might be able to get some direct cost same as above. Often, however, more value unlocks from the resulting reduction in Lead Time. Specifically, each day of Lead Time removed is worth items per year × value per item per day (example below). Even for processes that don't touch revenue directly, you can calculate a value per day from parent processes and then price your process' Lead Time contribution.
- **Completions per FTE did not change.** While individuals might have felt they were more productive, that extra output isn't translating to value. There is no ROI here, whatever the usage dashboard or the employee survey says. Most often this means an AI was placed at a step that wasn't the constraint, so the step behind it still limits output.

The reason companies fail to find an ROI of AI varies by each of the above outcomes:
- **Shadow Productivity**: In the first outcome, you can only count benefits if you harvest the cost. Many companies try to claim they got an "equivalent FTE's" worth but this is not operationally true unless that output yields more of a sellable product. But, because Demand was already being satisifed, that's not possible.
-**Missing Value**: In the second outcome, there are real, tangible benefits that your Finance team will not know how to measure. Namely, the team gets additional revenue from landing value-adding activities sooner. Imagine a bank who offers Payments Services to institutional customers. Fees flow as soon as the bank gets their systems live in the client. Those system integrations take time, however, and each extra day of Lead Time in the integration process is a day of lost revenue across _all new clients in a year_ (example below). Even processes 5 levels deep can place a value on their Lead Time by connecting to parent processes that make money (I call this a "Value Crossword" because of the shape the diagrams take).
- **Vanity AI**: The third outcome is a more extreme version of the first. At least in the first outcome the team was producing more output. In _this_ case, however, that's not even happening. Individuals might _feel_ like they are getting more done, and that might be true. However, by definition, none of that activity adds value unless it translates to an increase in output.

## One worked case

An investment bank earns an average of $300 per day from clients who use its institutional trading platform. Before a client can start using the platform (and before they start paying), they have to go through weeks-long onboarding process.

Unbeknonwst to the bank, that onboarding time had started slipping from 20 days, to 60.

- Completions had been lagging new deals by up to 25% for about a year.
- As a result, the number of open onboardings had almost doubled.
- As a result of that, the average time from deal close to client go-live had grown by about 40 days.

Each client earns about $302 per day once live, and the bank onboards about 5,673 clients a year. So every day added to onboarding lead time costs 5,673 × $302 ≈ **$1.7M a year**, and the 40 days that had crept in were costing about **$68M a year**. The bank would have needed roughly 617 extra sales to make that back.

The cause was a $1.8M cost saving taken elsewhere in the same function. Nobody had connected the headcount decision to the onboarding queue, because nobody was counting.

The fix was arithmetic too. The gap between Demand and Completions was about 53 items a month. At the team's measured rate of 7 completions per person per month, that is 8 people, at a cost of about $1.7M. $68M for $1.7M is a 38x return.

The 53 completions a month is also the target any AI deployed here would be measured against. If an AI closes that gap, its value can be stated two ways from the same counts: as 8 FTE-equivalents of capacity (about $1.7M, bankable the month it lands) and as 40 days of Lead Time (about $68M a year, visible once the queue clears). If it doesn't move Completions, it earned nothing, whatever it cost.

That last point is the whole method. Once you have the counts, "did the AI work" stops being a survey question and becomes a comparison of two numbers.

*(Chart placeholder: the six-panel page for this case — demand, completions, open items, lead time, completions per FTE, cost per completion.)*

## Why counting works where the usual approaches don't

Two things make the counts do work that KPIs and baselines haven't.

**Counts give you the value of a day.** Every process that touches revenue has a dollar value per day of lead time: items per year multiplied by value per item per day. Once you have it, you can price any delay anywhere in the chain, which turns "the approvals team is slow" into "the approvals team is adding 10 days to a $1.7M-a-day flow." Functions can be given targets in their own numbers without anyone allocating benefits top-down.

**Counts stop the most expensive mistake in cost-out.** When lead time halves, the instinct is to take out half the people. In almost every case the speed-up came from lower Open Items, and output per month did not change, so there is no spare capacity. Cut the people and Completions drop below Demand, the queue rebuilds, and both the original output and the speed gain are lost. The value of speed is on the revenue side: the same work earning sooner. You can see this in the counts before you make the cut.

The second half of the method is persuading a finance function to count the benefit. Only direct cost reduction is accepted by default. Revenue from earlier go-live, capacity released at a constraint, and reduced incidents are all trackable from the same counts, and each needs to be named and argued separately. The repo includes the material for that argument.

## Background: why ROI has been missing

Enterprise AI has an ROI problem that has changed shape three times.

In 2025 it looked like an execution problem. MIT reported that 95% of AI projects showed no financial return, which they attributed to where and how projects were chosen ([paper](https://mlq.ai/media/quarterly_decks/v0.1_State_of_AI_in_Business_2025_Report.pdf)). McKinsey's survey found returns concentrated in the 20% of companies doing AI "the right way" ([survey](https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai-how-organizations-are-rewiring-to-capture-value#/)).

In early 2026 it looked like a token economics problem. Companies rolling out AI at scale found token bills comparable to the salaries they hoped to replace, and the trade press moved from "tokenmaxxing" to "valuemaxxing" ([here](https://www.fastcompany.com/91590942/tokenmaxxing-is-out-valuemaxxing-is-in), [here](https://futurism.com/artificial-intelligence/ceos-reverse-course-ai-spending)).

By late 2026 the problem underneath both has become visible: companies cannot measure the return side at all. CIO Magazine explains why it's hard without offering a fix ([article](https://www.cio.com/article/4183502/why-is-it-so-hard-to-measure-the-roi-of-ai.html)). Deloitte describes rising investment and elusive returns ([report](https://www.deloitte.com/nl/en/issues/generative-ai/ai-roi-the-paradox-of-rising-investment-and-elusive-returns.html)). Fortune's story on CEO regret captures the mood ([story](https://fortune.com/2026/05/26/uber-coo-ai-spending-tokens-claude-code/)).

The reports that promise to solve this share a pattern ([McKinsey](https://www.mckinsey.com/capabilities/quantumblack/our-insights/where-ai-agents-pay-off-a-practical-guide-to-the-economics-of-agentic-workflows#/), [MIT Sloan](https://sloanreview.mit.edu/article/three-approaches-to-measuring-and-managing-ai-roi/)). They are precise about the investment, because cost is easy to add up. On the return they fall back to "tie to business KPIs" and "establish baselines," which every enterprise already does. The more sophisticated attempts rely on indirect measures such as employee surveys and benchmarks. One founder of an AI-ROI startup told me indirect measures were the only way to probe for a return.

It is reasonable to guess the measurement problem is causing a fair share of the execution problem. It is hard to put AI in the right place when you can't measure what "right" means.

## Who wrote this

I'm Ian Hill ([LinkedIn](https://www.linkedin.com/in/ianhill22/)). I've spent about twenty years on enterprise transformation at McKinsey, Microsoft, two large Australian banks, a quantum computing startup, and my own AI startup, and I now work in and advise large companies on AI transformation. Along the way I worked with or contracted several of the people whose ideas this builds on, including Jeff Sutherland, Don Reinertsen, and Douglas Hubbard.

The counting method came out of a longer question about why transformations fail at rates far higher than chance, across every industry and country, while a few classes of company reliably don't. The answer to that question is in the newsletters in this repo. The AI ROI method fell out of it almost as a side effect.

## What's in the repo

The folder structure may change, but the repo will hold:

- **This README**, as the explainer.
- **Slides** for learning the method and teaching it.
- **Charts with real data**, showing what the counts look like and how the arithmetic runs.
- **Case examples** from real clients, with as much concrete detail and data as can be shared.
- **Newsletters and longer writing**, for the theory and for applications beyond AI.
- **Skill files** that put all of the above in a form an LLM can use to walk you through the method on your own data.

## Using this material

Use anything here, as-is or modified, internally or in work for your own clients, including commercially. The one condition is attribution: refer to it prominently as the "Enthoosa approach" and include this repo's URL, rather than a footnoted name.

The repo is deliberately comprehensive so that re-using it with attribution is less work than re-badging it. I've had earlier work copied closely enough that the copy kept my typos, and I would rather make attribution the easy path than police it.

If the method works for you, a star helps other people find it.
