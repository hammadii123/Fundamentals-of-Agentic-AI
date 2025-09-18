

# Top-K in Prompt Engineering

---

## 1. What is Top-K?

When an AI generates text, it looks at all possible next words (**tokens**) with probabilities.

**Top-K** = AI only looks at the **K most likely words** and ignores the rest.
Then it chooses from those K candidates (often randomly, depending on temperature).

👉 **Simple analogy:**

* Without Top-K → you consider all ice cream flavors (even weird ones like garlic).
* With **Top-K = 3** → you only look at the top 3 flavors (chocolate, vanilla, strawberry).

So Top-K is like saying:

> “Don’t give me too many weird options, only pick from the best K ones.”

---

## 2. How Does It Work?

Sentence: `"The cat sat on the ..."`

| Token     | Probability |
| --------- | ----------- |
| mat       | 0.55        |
| floor     | 0.25        |
| chair     | 0.10        |
| table     | 0.07        |
| spaceship | 0.03        |

* **Top-K = 2:** Keeps {mat, floor} → Answer will be either “mat” or “floor.”
* **Top-K = 3:** Keeps {mat, floor, chair} → “chair” is also possible.
* **Top-K = 5:** Keeps all → even “spaceship” is possible.

---

## 3. Real-World Market Examples

**💻 Coding Assistants (GitHub Copilot, Cursor)**

* K = 1–2 → Consistent, correct code completions.
* K = 5+ → Multiple coding styles (loops, recursion, list comprehension).

**📞 Customer Service Chatbots (Banking, Airlines)**

* K = 1–2 → Only safe, standard responses.
* K = 5+ → More natural, varied replies.

**🎨 Marketing / Creative Writing**

* K = 1–3 → Professional, safe ad copy.
* K = 10+ → Creative, fun, unpredictable slogans.

**🎮 Gaming / Storytelling**

* K = 2 → NPC gives predictable, repeated dialogue.
* K = 8 → NPC says surprising things, making gameplay engaging.

---

## 4. Pros & Cons of Top-K

✅ **Pros:**

* Prevents rare/unwanted weird words.
* Keeps outputs more controlled & reliable.
* Balances safety and creativity.

❌ **Cons:**

* If K is too small (like 1) → AI becomes boring.
* If K is too big (like 50) → AI may produce nonsense.

---

## 5. Top-K vs Temperature

* **Temperature:** Controls *how random* the choice is.
* **Top-K:** Controls *how many options* AI can choose from.

👉 Often used together:

* **Low T + Small K** → Very safe, deterministic (good for coding).
* **High T + Large K** → Very creative, surprising (good for storytelling).

---

## 6. Python Coding Examples

**Example 1: Top-K with OpenAI**

```python
from openai import OpenAI
client = OpenAI()

response = client.chat.completions.create(
    model="gpt-4o-mini",
    temperature=0.7,        # randomness
    top_p=1.0,              # disable nucleus sampling
    messages=[
        {"role": "system", "content": "You are a creative story writer."},
        {"role": "user", "content": "Complete: The wizard opened the door and saw..."}
    ],
    extra_body={  
        "top_k": 3          # only keep top 3 tokens
    }
)

print(response.choices[0].message.content)
```

👉 **Possible Outputs (Top-K=3):**

* “…a dragon breathing fire.”
* “…a hidden treasure chest.”
* “…an old library of spells.”

It won’t say: “…a spaceship from Mars” (outside top-3).

---

**Example 2: Changing Top-K**

* **Top-K = 1** → Always “a dragon breathing fire.”
* **Top-K = 3** → {dragon, treasure, library} → some variation.
* **Top-K = 10** → Could even say “…a pizza delivery boy holding a wand.”

---

## 7. Industry Best Practices

| Use Case              | Top-K Value | Why?                      |
| --------------------- | ----------- | ------------------------- |
| Coding, SQL, Math     | 1–2         | Reliable, avoids mistakes |
| Customer Support      | 1–3         | Safe but natural replies  |
| Marketing / Ads       | 5–10        | Creative variations       |
| Storytelling / Gaming | 8–20        | Surprising, engaging      |
| Poetry / Jokes        | 20+         | Wild creativity           |

---

## 8. 50 MCQs on Top-K (with Answers)

---

### Basics

**1. Top-K controls:**

* a) Randomness
* ✅ **b) Number of options**
* c) Memory
* d) Speed

**2. If K=1, AI output is:**

* a) Creative
* ✅ **b) Deterministic**
* c) Nonsense
* d) Hallucinated

**3. If K=10, AI:**

* ✅ **a) Picks only from top 10 tokens**
* b) Picks from all tokens
* c) Ignores probabilities
* d) Always repeats

**4. Top-K works best when combined with:**

* a) Memory
* ✅ **b) Temperature**
* c) Context length
* d) System role

**5. In Top-K, lower K means:**

* a) More diversity
* ✅ **b) Less diversity**
* c) More speed
* d) More hallucination

---

### Applied Examples

**6. Customer support chatbots usually use:**

* ✅ **a) K=1–3**
* b) K=10
* c) K=50
* d) Unlimited

**7. Coding assistants like GitHub Copilot often set K:**

* ✅ **a) 1–2**
* b) 10
* c) 20
* d) 50

**8. Storytelling games prefer K around:**

* a) 1–2
* b) 3–5
* ✅ **c) 8–20**
* d) 50+

**9. If you want wild creative poetry, set:**

* a) K=1
* b) K=3
* ✅ **c) K=20+**
* d) K=2

**10. For SQL generation, best K is:**

* ✅ **a) 1**
* b) 5
* c) 10
* d) 20

---

### Theory Understanding

**11. Top-K filters words by:**

* a) Frequency
* ✅ **b) Probability**
* c) Length
* d) Syntax

**12. Without Top-K (K=∞):**

* a) Only 1 token considered
* ✅ **b) All tokens considered**
* c) Only 10 tokens considered
* d) Only top 5

**13. Top-K helps reduce:**

* a) Creativity
* ✅ **b) Rare words**
* c) Accuracy
* d) Context length

**14. Very large K may increase:**

* a) Repetition
* ✅ **b) Hallucination**
* c) Reliability
* d) Determinism

**15. Top-K is usually set between:**

* a) 0–1
* ✅ **b) 1–50**
* c) 100–200
* d) 500+

---

### Coding & Implementation

**16. In OpenAI API, Top-K is set in:**

* a) messages
* ✅ **b) extra\_body**
* c) model field
* d) tokens

**17. If Top-K=1 and T=0.0:**

* ✅ **a) Always same answer**
* b) Always random
* c) Creative
* d) Nonsense

**18. If Top-K=10 and T=1.0:**

* ✅ **a) More diverse outputs**
* b) Always same
* c) Zero randomness
* d) Faster responses

**19. In coding tasks, using K=10 may cause:**

* ✅ **a) Creative but risky code**
* b) Same output always
* c) Zero diversity
* d) Faster runtime

**20. In customer support, K too high can cause:**

* a) Friendly answers
* ✅ **b) Off-topic responses**
* c) Faster replies
* d) More accuracy

---

### Deeper Concept

**21. Top-K sampling discards tokens outside:**

* ✅ **a) Top probability group**
* b) Rare group
* c) Frequency group
* d) Hidden state

**22. If Top-K=3, AI only considers:**

* ✅ **a) Best 3 tokens**
* b) All tokens
* c) Tokens above 0.3 prob
* d) None

**23. Top-K ensures:**

* ✅ **a) Balance of safety and creativity**
* b) Always creativity
* c) Always randomness
* d) Always accuracy

**24. Top-K is a form of:**

* a) Regularization
* ✅ **b) Sampling**
* c) Optimization
* d) Encoding

**25. Which is more strict:**

* ✅ **a) K=1**
* b) K=10
* c) K=20
* d) K=50

---

## ✅ Key Takeaways

* **Top-K** filters options by keeping only the **K most likely tokens**.
* **Small K (1–2):** Safe, reliable, deterministic → Best for **coding, math, SQL**.
* **Medium K (5–10):** Balanced variation → Best for **customer support, marketing**.
* **Large K (20+):** Creative, surprising, sometimes weird → Best for **storytelling, poetry, jokes**.
* Works best **combined with Temperature** for fine-grained control.
