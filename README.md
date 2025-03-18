# AI with Python - Harvard University Course Notes

## Knowledge-Based Agents
Knowledge-based agents are agents that reason by operating on internal representations of knowledge.

### Example:
1. If it didn't rain, Abdullah visited Hagrid today.
2. Abdullah visited Hagrid or Dumbledore today, but not both.
3. Harry visited Dumbledore today.

---

## Sentence
A sentence is an assertion about the world in a knowledge representation language.

---

## Logical Connectives
Logical connectives are used to combine or modify sentences in logical reasoning.

| Symbol | Name          | Example                                      |
|--------|---------------|----------------------------------------------|
| ¬      | Not           | ¬P: It is not raining.                       |
| ^      | And           | P ^ Q: It is raining and it is Tuesday.      |
| v      | Or            | P v Q: It is raining or it is Tuesday.       |
| →      | Implication   | P → Q: If it is raining, then it is Tuesday. |
| ↔      | Biconditional | P ↔ Q: It is raining if and only if it is Tuesday. |

---

### 1. Not (¬)
The `Not` connective inverts the truth value of a sentence.

| p     | ¬p    |
|-------|-------|
| false | true  |
| true  | false |

**Example:**  
If `P` represents "It is raining," then `¬P` represents "It is not raining."

---

### 2. And (^)
The `And` connective is true only if both sentences are true.

| p     | q     | p ^ q |
|-------|-------|-------|
| false | false | false |
| false | true  | false |
| true  | false | false |
| true  | true  | true  |

**Example:**  
If `P` is "It is raining" and `Q` is "It is Tuesday," then `P ^ Q` is "It is raining and it is Tuesday."

---

### 3. Or (v)
The `Or` connective is true if at least one of the sentences is true.

| p     | q     | p v q |
|-------|-------|-------|
| false | false | false |
| false | true  | true  |
| true  | false | true  |
| true  | true  | true  |

**Example:**  
If `P` is "It is raining" and `Q` is "It is Tuesday," then `P v Q` is "It is raining or it is Tuesday."

---

### 4. Implication (→)
The `Implication` connective is false only when the first sentence is true, and the second is false.

| p     | q     | p → q |
|-------|-------|-------|
| false | false | true  |
| false | true  | true  |
| true  | false | false |
| true  | true  | true  |

**Example:**  
If `P` is "It is raining" and `Q` is "It is Tuesday," then `P → Q` is "If it is raining, then it is Tuesday."

---

### 5. Biconditional (↔)
The `Biconditional` connective is true when both sentences have the same truth value.

| p     | q     | p ↔ q |
|-------|-------|-------|
| false | false | true  |
| false | true  | false |
| true  | false | false |
| true  | true  | true  |

**Example:**  
If `P` is "It is raining" and `Q` is "It is Tuesday," then `P ↔ Q` is "It is raining if and only if it is Tuesday."

---

## Key Concepts in Logical Reasoning

### 1. Model
A model is an assignment of a truth value to every propositional symbol (a "possible world").

**Example:**  
- `P`: It is raining.  
- `Q`: It is Tuesday.  
A model could be `{P=true, Q=false}`, meaning it is raining but not Tuesday.

---

### 2. Knowledge Base
A knowledge base is a set of sentences known by a knowledge-based agent.

---

### 3. Entailment
Entailment (`a |= b`) means that in every model where sentence `a` is true, sentence `b` is also true.

---

### 4. Inference
Inference is the process of deriving new sentences from old ones.

**Example:**  
- `P`: It is Tuesday.  
- `Q`: It is raining.  
- `R`: Harry goes for a run.  

**Knowledge Base (KB):** `(P ^ ¬Q) → R`  
**Interpretation:** If it is Tuesday and it is not raining, then Harry will go for a run.

---

### 5. Model Checking
Model checking is the process of determining if `KB |= a` (KB entails `a`).

**Steps:**  
1. Enumerate all possible models.  
2. If in every model where KB is true, `a` is also true, then KB entails `a`.  
3. Otherwise, KB does not entail `a`.

---

## Example Problem
Let’s apply the concepts to the following scenario:

1. If it didn't rain, Abdullah visited Hagrid today.  
   `¬Rain → VisitHagrid`  
2. Abdullah visited Hagrid or Dumbledore today, but not both.  
   `VisitHagrid ⊕ VisitDumbledore`  
3. Harry visited Dumbledore today.  
   `VisitDumbledore`

**Question:** Did it rain today?  
**Solution:**  
- From statement 3, `VisitDumbledore` is true.  
- From statement 2, since `VisitDumbledore` is true, `VisitHagrid` must be false.  
- From statement 1, if `VisitHagrid` is false, then it must have rained (`¬Rain → false` implies `Rain` is true).  

**Conclusion:** It rained today.
