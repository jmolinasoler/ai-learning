<https://x.com/i/status/2048418646960288059>
**Video Summary**  
This is a ~24-minute free workshop from Anthropic’s own team (the creators of Claude) on practical **prompt engineering**. It’s not theory-heavy — it’s a live, hands-on demo showing exactly how to build powerful prompts from scratch inside the Claude console.

They use one clear real-world example throughout: analyzing photos of a Swedish accident report form (a multi-column, somewhat messy document with checkboxes, handwriting, and Swedish text). Starting with a basic prompt, they iteratively improve it through 5+ versions (v1 → v5), showing how small, deliberate changes dramatically improve accuracy, structure, and reliability. You watch the prompt evolve in real time, with side-by-side comparisons of outputs.

The format mixes:

- Slide explanations of core concepts
- Console demos
- Live audience Q&A (auditorium setting)
- Practical techniques you can copy-paste immediately

It’s exactly what the poster says: worth more than most $300 courses because it comes straight from the people who built Claude.

**Key Wisdom Extracted (the real gold)**

1. **Prompt engineering is a skill, not magic**  
   It’s “the practice of systematically improving prompts through testing, evaluation, analysis, and optimization.”  
   Required skills: clear/unambiguous writing, conceptual engineering, scientific mindset (test → measure → iterate), product thinking (what does the ideal output look like for your use case?), and deep understanding of how LLMs actually work.

2. **Iterate ruthlessly in the console**  
   Don’t write the perfect prompt in one shot. Build it step by step:  
   - Start with the task  
   - Add role/context  
   - Give explicit output format  
   - Add reasoning instructions  
   - Add safeguards  
   - Test on edge cases  
   Each version in the video visibly gets better.

3. **Hallucination prevention toolkit** (explicitly taught)  
   - Tell Claude: “If you don’t know, say ‘I don’t know.’”  
   - Ask it to only answer if it is *very confident*.  
   - Force it to “think before answering” (chain-of-thought).  
   - Make it quote relevant parts of the source material first, then answer based on the quotes.

4. **Image/document analysis super-prompt pattern** (the core example)  
   They refine the prompt to:  
   - Describe what the image actually shows  
   - Extract data with high precision  
   - Flag uncertainty  
   - Follow strict formatting rules  
   - Ignore irrelevant noise  
   The final prompt turns Claude into a reliable data-entry + reasoning engine for messy real-world forms.

5. **Extended thinking vs. classic prompt engineering**  
   The workshop contrasts two powerful modes:  
   - Classic prompt engineering = precise instructions, structure, safeguards  
   - Extended thinking = giving Claude time/space to reason step-by-step internally (especially useful for complex analysis)

6. **Mindset shift**  
   Stop treating Claude like a search engine or chatbot. Treat it like a highly capable but literal colleague who needs crystal-clear instructions, context, and quality-control mechanisms. The people who built it emphasize that *most users are leaving 80% of Claude’s capability on the table* by using basic prompts.

**Bottom line**  
This workshop is the closest thing to “official Anthropic prompting training” that exists for free. Watch it once, bookmark it, and you’ll instantly level up every interaction you have with Claude (and honestly any other frontier model). The iterative, example-driven style is way more valuable than any generic “100 best prompts” list.

The poster also links to a companion guide right below the video — highly recommended after watching, as it probably contains the exact final prompts shown.

**Chain-of-Thought (CoT) prompting** is a powerful prompt engineering technique that significantly improves how large language models (LLMs) handle complex reasoning tasks. Instead of jumping straight to a final answer, the model is guided to break down the problem into a series of **intermediate reasoning steps**—essentially showing its "thinking" process before concluding.

This mimics how humans solve problems: we rarely get the right answer instantly on hard questions; we reason step by step, check assumptions, calculate intermediates, and synthesize.

### Why It Works

LLMs are trained on vast text data, including examples of people thinking aloud (e.g., tutorials, explanations, math solutions). By explicitly prompting the model to generate a "chain" of logical steps, you activate and steer this latent capability. Research (notably the 2022 paper by Wei et al.) showed that CoT dramatically boosts performance on arithmetic, commonsense, symbolic, and multi-step reasoning tasks—especially in larger models where this ability emerges more strongly.

Without CoT, models often rely on pattern matching and can hallucinate or make leaps. With CoT, outputs become more accurate, transparent, and debuggable because you can see (and correct) where the reasoning goes wrong.

### Two Main Variants

1. **Few-Shot CoT** (with examples)  
   You provide 1–several complete examples in the prompt: the question + a detailed step-by-step reasoning chain + the final answer.  
   The model then mimics that structure for the new question.  
   This is especially effective for consistent, domain-specific reasoning.

2. **Zero-Shot CoT** (no examples needed)  
   Simply add a short instruction like:  
   - “Let’s think step by step.”  
   - “Work this out in a step-by-step way to be sure we have the right answer.”  
   - “First, understand the problem. Then break it down logically...”  

   This is surprisingly effective and much easier to use.

### Simple Examples

**Without CoT** (prone to error):  
Q: Roger has 5 tennis balls. He buys 2 more cans of tennis balls. Each can has 3 tennis balls. How many tennis balls does he have now?  
A: 11 tennis balls.

**With Zero-Shot CoT**:  
Q: [same question]  
Let’s think step by step.  
A: Roger started with 5 balls.  
2 cans × 3 balls per can = 6 balls.  
Total: 5 + 6 = 11 tennis balls.

**With Few-Shot CoT**, you’d include 2–3 similar solved examples before the actual question to guide the format and depth of reasoning.

### Best Practices for Effective CoT Prompting

- **Be explicit**: Tell the model exactly what kind of steps to take (e.g., “List all assumptions first,” “Calculate each intermediate value,” “Quote relevant parts of the source before reasoning”).
- **Structure the output**: Use numbered steps, tags like `<thinking>...</thinking>`, or clear sections (e.g., “Step 1: Understand the problem. Step 2: ... Final Answer:”).
- **Combine with other techniques**: Pair CoT with role assignment (“You are a careful mathematician”), output formatting instructions, or safeguards (“If uncertain, say so and explain why”).
- **Use it when needed**: Great for math, logic puzzles, analysis, planning, debugging, or any multi-step task. Skip it for simple factual queries to save tokens and time.
- **Iterate and test**: As shown in the Anthropic workshop you watched earlier, start basic and refine—add more guidance on reasoning quality, verification steps, or handling edge cases.
- **Verification**: Add a final step like “Now double-check your reasoning and confirm the answer satisfies all conditions.”

### Relation to Claude / Anthropic Techniques

In the context of the Anthropic prompt engineering workshop (the video you shared), CoT aligns closely with their emphasis on **“thinking before answering”** and iterative prompt improvement. Claude supports classic CoT via prompts, and newer versions include **extended thinking** (a built-in mode that allocates extra compute for deeper internal reasoning, sometimes with visible “thinking” blocks). Extended thinking is like an enhanced, model-native version of CoT—it gives the model more “time” and tokens to reason internally before responding.

The workshop likely demonstrated how adding explicit step-by-step instructions (lightweight CoT) turns Claude from a quick responder into a more reliable analyst—especially useful for messy documents like the Swedish accident forms in their demo.

### Bottom Line Wisdom

Chain-of-thought prompting is one of the highest-leverage, simplest techniques in prompt engineering. It costs a bit more in tokens (because of the extra reasoning text) but often delivers disproportionately better results on anything non-trivial. The key mindset: treat the LLM like a smart but sometimes hasty colleague—force it to show its work, and you’ll catch errors, build trust, and unlock much higher performance.

Try it yourself: Take any complex question you have, add “Let’s think step by step,” and compare the output to a direct ask. You’ll quickly see the difference. For even stronger results, combine it with the iterative refinement approach from the Anthropic session.

**Tree-of-Thoughts (ToT) prompting** is an advanced prompt engineering technique that builds directly on **Chain-of-Thought (CoT)**. While CoT guides an LLM along a single linear reasoning path (step-by-step thinking), ToT creates a **tree-like structure** of multiple possible reasoning paths. The model explores several branches in parallel, evaluates them, and can look ahead, backtrack, or prune less promising paths—mimicking deliberate human problem-solving with trial-and-error, planning, and strategic exploration.

It was introduced in the 2023 paper *"Tree of Thoughts: Deliberate Problem Solving with Large Language Models"* by Shunyu Yao et al. The core idea is to treat "thoughts" as coherent units of text (intermediate reasoning steps or partial solutions) and search over a tree of these thoughts using algorithms like breadth-first search (BFS), depth-first search (DFS), or beam search.

### How Tree-of-Thoughts Works

ToT typically involves these key steps (often implemented across multiple LLM calls or in a structured single prompt):

1. **Thought Generation**: From the current state (problem or partial solution), generate multiple candidate "thoughts" — different next steps, ideas, or partial solutions (e.g., 3–5 branches per node).

2. **Self-Evaluation**: The model scores or evaluates each thought for promise, progress toward the goal, or quality (e.g., "Rate this step from 1–10 on how likely it leads to a solution").

3. **Search & Decision**: Use a search strategy to decide which branches to explore further:
   - **Breadth-First**: Explore all promising options at the current level before going deeper.
   - **Depth-First**: Dive deep into one promising path, backtracking if it fails.
   - Lookahead (simulate future steps) or backtracking when a path hits a dead end.

4. **Pruning & Convergence**: Discard low-value branches and continue until a strong solution emerges or a depth limit is reached.

This turns reasoning into an explorative search process rather than a one-shot linear chain.

### Simple Comparison: CoT vs. ToT

| Aspect              | Chain-of-Thought (CoT)                  | Tree-of-Thoughts (ToT)                          |
|---------------------|-----------------------------------------|-------------------------------------------------|
| Structure          | Linear (single path)                   | Tree (multiple branching paths)                |
| Exploration        | One reasoning sequence                 | Parallel exploration + evaluation              |
| Error Handling     | Prone to early mistakes derailing everything | Can backtrack and try alternatives             |
| Best For           | Sequential logic, math, straightforward analysis | Complex planning, puzzles, creative strategy, ambiguous problems |
| Cost/Complexity    | Lower (fewer tokens, single prompt)    | Higher (multiple calls or longer prompts)      |

ToT shines when a single wrong assumption in a linear chain would ruin the outcome. It allows the model to consider "what if" alternatives systematically.

### Practical Examples

**Basic ToT Prompt Pattern** (zero-shot style, works in one conversation):

```
Solve this problem using Tree of Thoughts reasoning.

Problem: [Your question]

Step 1: Generate 3 different possible first thoughts/steps toward solving it.
For each, briefly explain why it might work.

Step 2: Evaluate each of the 3 thoughts on a scale of 1-10 for promise. Explain your scoring.

Step 3: Choose the most promising thought and generate 2-3 next-step branches from it.

Repeat the evaluation and expansion process for 2-3 levels, then select the best overall path and give the final solution with full reasoning.
```

**Expert Simulation Variant** (popular simple implementation):

```
Imagine three different experts are answering this question. All experts will write down 1 step of their thinking, then share it with the group. They will then discuss and vote on the best next step. Continue this process until the problem is solved.
```

**Classic Benchmark Example** (Game of 24 puzzle):

- Task: Use four numbers (e.g., 4, 9, 10, 13) exactly once with +, -, ×, ÷ to make 24.
- CoT might try one sequence and fail if early choice is bad.
- ToT generates multiple initial combinations, evaluates viability (lookahead to see if it can reach 24), prunes dead ends, and explores deeper on promising ones. In the original paper, ToT boosted success rates dramatically (e.g., from ~4% with CoT to 74% in some tests with GPT-4).

### Best Practices for Effective ToT

- **Define clear evaluation criteria** — Tell the model exactly how to score thoughts (relevance, feasibility, progress, consistency with facts).
- **Limit branching factor** — Usually 2–5 thoughts per node to control token usage and avoid explosion.
- **Set depth limits** — Prevent infinite exploration (e.g., max 3–5 levels).
- **Combine with other techniques** — Use roles ("You are a strategic planner"), output formatting (structured sections with scores), or safeguards ("If no path works, explain why").
- **Implementation options**:
  - Simple: One long prompt guiding the tree process (good for Claude/ChatGPT).
  - Advanced: Multi-turn conversation or code wrapper (agentic setup with BFS/DFS logic calling the LLM repeatedly).
- **When to use**: Complex planning, creative writing ideation, puzzle-solving, strategic decision-making, debugging ambiguous code, or any task with high branching uncertainty. Skip for simple factual or linear tasks (CoT or direct prompting is more efficient).

### Relation to Claude & the Anthropic Workshop

In the Anthropic prompt engineering workshop you watched (focused on iterative refinement for document analysis), the emphasis was on classic techniques like explicit instructions, output formatting, and "thinking before answering" (light CoT). ToT is a natural next-level extension for more exploratory tasks.

Claude models handle ToT-style prompting very well due to their strong reasoning and instruction-following abilities. Newer Claude versions also support built-in "thinking" or adaptive thinking modes (allocating extra compute for deeper reflection), which can complement ToT by enhancing internal evaluation of branches. Anthropic's own guidance stresses structured, deliberate reasoning — ToT fits perfectly as a way to make that more systematic and robust.

### Bottom Line Wisdom

Tree-of-Thoughts elevates prompting from "follow this one chain" to "explore the solution space intelligently." It's more powerful than basic CoT for hard, non-linear problems but comes at the cost of higher complexity and token usage. Start simple with guided multi-branch prompts, then iterate (as the Anthropic team demonstrated in their workshop). The real power comes from combining it with self-evaluation and search-like decision making.

Test it yourself: Take a tricky puzzle or planning task (e.g., "Plan a 3-day trip with constraints"), apply a basic ToT prompt, and compare to plain CoT. You'll often see richer exploration and better final outcomes.

If you want a ready-to-copy template for a specific use case or examples tailored to Claude, just let me know!
