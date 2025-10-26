# Chain-of-Thought Prompting 

This paper discusses a trick for “making large models think better at low cost”: when asking questions, don’t just request the answer; instead, include a few examples with detailed solution steps in the prompt. The author calls this approach **Chain-of-Thought prompting (CoT)**. With these demonstrations, the model is more likely to follow a “think step by step before answering” approach on new problems, often significantly improving accuracy on complex questions.

**Why it works.** The chain of thought breaks down a difficult problem that would normally be taken in one big bite into smaller steps: first extracting conditions, then setting intermediate variables, and gradually performing calculations or eliminations. For large models, this structured process signal is easier to learn and reuse than “directly supplying the final answer.”

**Ruling out the “more words help” myth.** The paper ran control experiments showing that merely asking the model to first write an equation, or to output meaningless placeholders, or even to give the answer first and then fill in the process, is not as effective as genuinely writing out the reasoning step by step in natural language. The key is *step-by-step reasoning*, not word count.

**Where it helps most.** In tasks such as elementary school word problems, commonsense reasoning, and symbolic reasoning, CoT prompts generally outperform standard prompts; the more multi-step reasoning a task requires, the greater the benefit. For simple problems solvable in one step, the improvement is minimal or even nonexistent.

**Scale threshold.** The paper identifies a “scale threshold”: small models, even when given CoT examples, often produce sentences that are fluent but logically incorrect; only when the model reaches a scale of tens of billions of parameters does the advantage of CoT truly “emerge,” yielding substantial accuracy gains.

**Length extrapolation.** The paper also reports a phenomenon of **length extrapolation**: with CoT, large models can generalize the step-by-step strategy from shorter training-style examples to longer reasoning chains at test time.
