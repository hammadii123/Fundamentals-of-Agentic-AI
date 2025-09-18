# Temperature in Prompt Engineering

## 1. What is Temperature?

Think of temperature as a **creativity level of AI**.
It decides how the AI picks words when it answers you.

- **Low temperature (close to 0)** → AI gives safe, predictable answers.
- **High temperature (closer to 1 or more)** → AI gives creative, surprising answers.

---

## 2. Simple Analogy (Daily Life)

Imagine you are choosing food at a restaurant:

- **T = 0.0** → You always order the same dish (safe).
- **T = 0.3** → You mostly order your favorite dish but sometimes try another.
- **T = 0.7** → You try different dishes every time.
- **T = 1.2** → You may even order something totally unexpected or weird!

So, temperature = how adventurous you are.

---

## 3. How Does It Work Inside the AI?

AI doesn’t “know the answer directly.” It looks at a list of possible next words with probabilities.

Example: You type → "The cat sat on the..."

- mat → 60% chance

- floor → 20% chance

- chair → 10% chance

- moon → 10% chance

- **If T = 0.1 (low):** AI almost always picks “mat.”

- **If T = 1.0 (normal):** AI might pick mat, floor, or chair.

- **If T = 2.0 (high):** Even “moon” could be chosen!

So, temperature changes how strict or free AI is when choosing.

---

## 4. Real Market Examples with Agentic AI

### Example 1: Coding Assistant (GitHub Copilot / Cursor / Replit)

**Code:**

```python
from openai import OpenAI
client = OpenAI()

response = client.chat.completions.create(
    model="gpt-4o-mini",
    temperature=0.2,
    messages=[
        {"role": "system", "content": "You are a coding assistant."},
        {"role": "user", "content": "Write a Python function to reverse a string."}
    ]
)

print(response.choices[0].message.content)
```

**Response (Low T = 0.2, Safe & Predictable):**

```python
def reverse_string(s: str) -> str:
    return s[::-1]
```

**If we set temperature=1.0 (Creative):**

```python
def reverse_string(s: str) -> str:
    # Using recursion for fun
    if len(s) == 0:
        return s
    else:
        return reverse_string(s[1:]) + s[0]
```

**Market Relevance:**

- GitHub Copilot → keeps T low for correctness.
- Replit Ghostwriter → may use higher T for creative alternatives.

---

### Example 2: Customer Support Bot (Banks vs E-commerce)

- **Low Temperature (T=0.3):**
  User: “What’s my account balance?”
  AI: “Your current account balance is \$1,250.43.”

- **Medium Temperature (T=0.6):**
  AI: “Your account balance is \$1,250.43. Do you want me to also show your last 3 transactions?”

- **High Temperature (T=1.0):**
  AI: “Looks like your balance is \$1,250.43. Want me to share a cool saving tip too?”

**Market Examples:**

- Banks (JPMorgan, Citibank AI bots) → use low T.
- E-commerce (Amazon, Shopify stores) → use medium T.

---

### Example 3: Marketing & Ad Copy (Coca-Cola, Nike, Shopify)

**Code:**

```python
response = client.chat.completions.create(
    model="gpt-4o",
    temperature=1.0,
    messages=[
        {"role": "system", "content": "You are a creative ad writer."},
        {"role": "user", "content": "Write a catchy slogan for a sports drink."}
    ]
)
print(response.choices[0].message.content)
```

**Response (High T = 1.0, Creative):**
“Fuel your hustle. Refresh your power.”

**Response (Low T = 0.2, Boring but Safe):**
“A sports drink to keep you hydrated during exercise.”

**Market Relevance:**

- Coca-Cola AI marketing labs → use high T.
- Shopify merchants → often use high T for unique product descriptions.

---

### Example 4: News Summarization (Notion AI vs Buzzfeed)

**Input:** “Summarize today’s stock market news.”

- **Low T (0.2):**
  “Stock markets closed higher today. The S\&P 500 gained 1.2%, led by tech stocks. Investors reacted positively to the Fed’s comments on interest rates.”

- **High T (1.0):**
  “Wall Street roared back today. Tech giants fueled a rally as investors cheered the Fed’s softer stance on rates.”

**Market Relevance:**

- Notion AI, Perplexity → low T for factual summaries.
- Buzzfeed, Tabloid news AI → high T for catchy headlines.

---

### Example 5: Gaming & Storytelling Agents (AI Dungeon, Role-Playing Games)

**User Prompt:** “The knight enters a dark forest. What happens next?”

- **Low T (0.3):**
  “The knight walks carefully through the forest. He hears the sound of birds and the rustling of leaves.”

- **High T (1.2):**
  “The knight steps into the shadowy forest, only to be greeted by glowing eyes in the trees. A talking wolf whispers: ‘You are not welcome here…’”

**Market Example:**
AI Dungeon uses high T to keep the story unpredictable.

---

## 5. Agentic AI Context (Why Temperature Matters)

In **Agentic AI** (AI agents that plan, use tools, and make decisions):

- **Low T Agents:** For structured tasks (coding, SQL, finance, healthcare).
- **Medium T Agents:** For teaching, onboarding, tutoring.
- **High T Agents:** For entertainment, marketing, creative ideation.

---

## 6. Pros & Cons

**Pros**

- **Low Temperature:** Safe, repeatable answers. Great for coding, math, legal writing.
- **High Temperature:** Creative, fun, diverse answers. Good for stories, brainstorming, marketing.

**Cons**

- **Low Temperature:** Boring, robotic, repetitive.
- **High Temperature:** Risky → AI may give nonsense or hallucinate. Not good for serious tasks (finance/medicine).

---

## 7. Best Practices (Industry Usage)

| Task                  | Best Temperature | Why                          |
| --------------------- | ---------------- | ---------------------------- |
| Coding / SQL / Math   | 0.0 – 0.3        | Needs correctness            |
| Customer Support      | 0.3 – 0.6        | Safe but still human-like    |
| Brainstorming Ideas   | 0.5 – 0.8        | Mix of logic + creativity    |
| Storytelling / Poetry | 0.8 – 1.2        | Needs variety & creativity   |
| Games / Jokes / Fun   | 1.0 – 1.5        | Unpredictable & entertaining |

---

## 8. Easy Daily Analogy (Spice Level in Food)

- **0.0 = No spice at all** → very plain food (safe but boring).
- **0.5 = Medium spice** → balanced (tasty and safe).
- **1.0 = Extra spicy** → fun but can burn your mouth!
- **2.0 = Over spicy** → chaos, too much to handle.

Temperature works exactly like spice.

---

## 9. Final Summary

- Temperature = AI’s **creativity knob**.
- **Low T** = safe, reliable but boring.
- **High T** = creative, risky but fun.
- Choose temperature **based on your task**.

---

Perfect — I’ll create the **full README.md** with all 50 MCQs, correct answers in **bold**, and all your original bracketed explanations intact.

---

Perfect — I’ll polish your **README.md** so it looks clean, professional, and attractive. I’ll improve:

* Proper **spacing & indentation**
* Consistent **options alignment (a), b), c), d))**
* Clear separation between **questions and answers**
* Headings and sections visually neat

Here’s the refined version:

---
Perfect, I’ll keep the same clean **README style** you approved, but now I’ll add a ✅ emoji to make the **correct MCQs more prominent**.
Here’s the **full 50 MCQs** completed in that format:

---

# Temperature in LLMs – 50 MCQs with Answers & Explanations

---

## Basics

**1. Temperature in LLMs controls:**

* a) Speed
* ✅ **b) Randomness (Because temperature adjusts how randomly tokens are chosen during generation.)**
* c) Accuracy
* d) Memory

**2. A temperature of 0 means:**

* a) Always random
* ✅ **b) Deterministic (Because at T=0, the model always picks the highest probability token.)**
* c) Creative
* d) Nonsense

**3. Temperature modifies:**

* a) User prompt
* ✅ **b) Token logits (Because logits are divided by T before softmax to adjust probability spread.)**
* c) Training data
* d) Context window

**4. Which formula includes temperature?**

* ✅ **a) P = exp(logit/T) / Σ exp(logit/T) (This is the softmax with temperature scaling.)**
* b) P = logit × T
* c) P = logit + T
* d) None

**5. Higher temperature makes the distribution:**

* a) Sharper
* ✅ **b) Flatter (Because probabilities spread out, making rare tokens more likely.)**
* c) Narrower
* d) More peaked

---

## Practical Ranges

**6. Best range for deterministic factual answers:**

* ✅ **a) 0.0–0.3 (Low T keeps answers consistent and factual.)**
* b) 0.5–0.7
* c) 0.8–1.0
* d) >1.5

**7. Best range for story generation:**

* a) 0.0–0.2
* b) 0.4–0.7
* ✅ **c) 0.8–1.2 (Higher T encourages creativity and variation in storytelling.)**
* d) >2.0

**8. What happens at very high T (>2)?**

* a) Outputs coherent always
* ✅ **b) Outputs more random, often nonsense (Very high T makes output unstable and meaningless.)**
* c) Outputs deterministic
* d) Output length decreases

**9. A chatbot in healthcare should use:**

* ✅ **a) T=0.0 (Healthcare needs accuracy and determinism, no randomness.)**
* b) T=0.9
* c) T=1.5
* d) T=2.0

**10. A poetry generator should use:**

* a) 0.1
* b) 0.5
* ✅ **c) 0.9 (Poetry benefits from creativity and variation, which comes from higher T.)**
* d) 0.0

---

## Effects on Output

**11. Low temperature answers are:**

* a) Creative
* ✅ **b) Consistent (They stick to the most likely token paths.)**
* c) Random
* d) Chaotic

**12. High temperature answers are:**

* a) Predictable
* b) Always correct
* ✅ **c) More diverse (Because probability mass spreads across multiple tokens.)**
* d) Deterministic

**13. If a student asks a math problem, ideal T is:**

* a) 1.0
* b) 0.8
* ✅ **c) 0.0 (Math needs accuracy and consistency, no randomness.)**
* d) 1.5

**14. For brainstorming new startup ideas, best T is:**

* a) 0.0
* ✅ **b) 0.9 (Higher T encourages creative idea generation.)**
* c) 0.2
* d) 0.5

**15. Temperature directly influences:**

* ✅ **a) Token selection probabilities (Because it reshapes the probability distribution.)**
* b) Model weights
* c) Context length
* d) Training epochs

---

## Comparisons

**16. Temperature vs Top-k:**

* ✅ **a) Temperature smooths probabilities, Top-k cuts them off.**
* b) Both do the same
* c) Top-k is always better
* d) Temperature is about memory

**17. Temperature = 0.5 vs 1.0, which is more stable?**

* ✅ **a) 0.5 (Lower T → more stable answers.)**
* b) 1.0
* c) Both same
* d) Cannot say

**18. Temperature is applied during:**

* a) Training
* ✅ **b) Inference (It changes probabilities when generating outputs, not when learning.)**
* c) Data preprocessing
* d) Fine-tuning

**19. Which is true?**

* ✅ **a) T=0 makes outputs repeatable (Because the highest probability token is always chosen.)**
* b) T=0 makes outputs random
* c) T=1.5 is deterministic
* d) T doesn’t affect randomness

**20. Temperature mainly impacts:**

* a) Memory recall
* ✅ **b) Creativity vs determinism (It balances novelty with reliability.)**
* c) Context length
* d) Latency

---

## Real-world Applications

**21. News summarization requires:**

* ✅ **a) Low T (Factual, concise, consistent summaries are needed.)**
* b) High T
* c) Medium T
* d) Very high T

**22. Writing jokes needs:**

* a) 0.0
* b) 0.3
* ✅ **c) 0.9 (Humor benefits from creativity and unexpected associations.)**
* d) 2.0

**23. Scientific paper Q\&A should use:**

* ✅ **a) 0.0–0.2 (Ensures factual, repeatable answers.)**
* b) 0.5
* c) 1.0
* d) 1.5

**24. Fantasy story continuation should use:**

* a) 0.1
* b) 0.3
* ✅ **c) 1.0 (Balanced creativity for storytelling.)**
* d) 2.0

**25. Legal document drafting needs:**

* ✅ **a) 0.0 (Precision and determinism are critical in law.)**
* b) 0.6
* c) 1.0
* d) 1.5

---

## Advanced

**26. Increasing T > 1 does what?**

* a) Makes probabilities sharper
* ✅ **b) Makes distribution flatter (Even rare tokens get more chance.)**
* c) No effect
* d) Increases context

**27. Decreasing T < 1 does what?**

* ✅ **a) Sharpens probabilities (Model prefers top tokens more strongly.)**
* b) Flattens distribution
* c) Increases creativity
* d) Randomizes

**28. Temperature cannot be:**

* a) 0
* b) 0.5
* ✅ **c) Negative (Because dividing by negative T breaks probability logic.)**
* d) 2.0

**29. If model is repetitive, solution is:**

* a) Lower T
* ✅ **b) Increase T (Higher T reduces repetition by adding randomness.)**
* c) Decrease context
* d) Restart training

**30. If model is incoherent, solution is:**

* ✅ **a) Lower T (Brings answers closer to most probable tokens.)**
* b) Increase T
* c) Increase context
* d) Add memory

---

## Technical

**31. Temperature modifies logits before:**

* a) Training
* ✅ **b) Softmax (Logits are divided by T before applying softmax.)**
* c) Embedding
* d) Attention

**32. With T=0.7, compared to T=0.2:**

* a) More deterministic
* ✅ **b) More diverse outputs (Because probabilities are more spread out.)**
* c) Less creative
* d) Always longer answers

**33. If two tokens have probabilities 0.8 and 0.2, at T=0:**

* ✅ **a) Token with 0.8 always chosen (Deterministic maximum likelihood.)**
* b) Token with 0.2 sometimes chosen
* c) Random
* d) Both chosen

**34. If T=1.0, distribution is:**

* ✅ **a) Original probabilities (No scaling effect at T=1.)**
* b) Always uniform
* c) Always sharp
* d) Always flat

**35. If T → ∞, distribution approaches:**

* a) Sharp
* ✅ **b) Uniform (All tokens equal chance, complete randomness.)**
* c) Deterministic
* d) Context-based

---

## Case Studies

**36. Chatbot for banking should use:**

* ✅ **a) Low T (Banking needs factual, precise responses.)**
* b) High T
* c) Very high T
* d) Doesn’t matter

**37. Rap lyric generation should use:**

* a) 0.0
* b) 0.3
* ✅ **c) 1.0 (Encourages rhymes, creativity, variety.)**
* d) 2.0

**38. Translation task should use:**

* ✅ **a) Low T (Because translation must be accurate and repeatable.)**
* b) 0.9
* c) 1.5
* d) 2.0

**39. Writing ad slogans should use:**

* a) 0.1
* b) 0.3
* ✅ **c) 0.8 (Creativity needed for catchy slogans.)**
* d) 2.0

**40. Debugging code task should use:**

* ✅ **a) 0.0 (Code debugging must be precise, not random.)**
* b) 0.7
* c) 1.0
* d) 2.0

---

## Mixed Knowledge

**41. Temperature affects:**

* a) Model training
* ✅ **b) Inference-time randomness**
* c) Attention heads
* d) Embedding size

**42. Temperature can be combined with:**

* ✅ **a) Top-k & Top-p sampling (They often work together to balance randomness and control.)**
* b) Context window
* c) Model weights
* d) Dataset size

**43. Lowering T reduces:**

* a) Accuracy
* ✅ **b) Diversity (Answers become repetitive and predictable.)**
* c) Consistency
* d) Coherence

**44. Raising T increases:**

* a) Stability
* ✅ **b) Randomness (The model explores less probable tokens.)**
* c) Factual accuracy
* d) Memory size

**45. In deterministic tasks, T should be:**

* ✅ **a) Low (Deterministic tasks need repeatable answers.)**
* b) High
* c) Random
* d) Medium

---

## Final

**46. In brainstorming tasks, T should be:**

* a) 0.0
* b) 0.3
* ✅ **c) High (Creativity requires randomness.)**
* d) Negative

**47. In legal advice tasks, T should be:**

* ✅ **a) Low (Legal requires precision and consistency.)**
* b) High
* c) Medium
* d) Infinite

**48. If two runs give different answers, likely T was:**

* ✅ **a) >0 (Any T above 0 introduces randomness.)**
* b) 0
* c) Negative
* d) Ignored

**49. Which is true about T=0?**

* ✅ **a) Greedy decoding (Always picks max probability token.)**
* b) Random sampling
* c) Uniform distribution
* d) No answer

**50. Key takeaway:**

* ✅ **a) Low T → factual & stable, High T → creative & diverse**
* b) High T → stable, Low T → random
* c) T has no impact
* d) T affects training only

