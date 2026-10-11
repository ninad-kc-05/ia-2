**Course:** Artificial Intelligence & Soft Computing  
**Question bank:** Modules 4, 5 and 6  
**Purpose:** Exam-oriented theory preparation. The four ANN numericals (QB Q5–Q8) are deliberately kept in a separate practice track.

## Study strategy

1. Master Module 4 numericals separately, while learning the ANN theory needed to understand them.
2. Prepare 7-mark theory first: Module 5, then Module 6.
3. Cover Module 4's 2-mark theory.
4. Finish Module 5 and Module 6's 2-mark theory.

### Source labels

- **College notes / syllabus / QB:** Directly based on the uploaded AISC syllabus, Module 4 college notes and IA-2 question bank.
- **Reference Deep Dive:** Expanded using the uploaded reference books where the syllabus/QB only names the topic. The answers are exam-oriented summaries, not verbatim textbook extracts.

---

# PRIORITY 1 — MODULE 5: 7-MARK THEORY

## Q13. Analyze how associative memory retrieves stored information using a suitable example. (7 marks)

**Ideal Answer**

### Definition
An **associative memory network** is a neural network that stores patterns and retrieves an associated pattern when it receives a complete or partial input pattern.

### Working mechanism
1. **Storage:** The network is trained or configured to store associations between patterns.
2. **Input:** A stored pattern, or a noisy/incomplete version of it, is presented to the network.
3. **Comparison and processing:** The network processes the input using its stored connection weights.
4. **Association/retrieval:** The network produces the pattern associated with the input.
5. **Correction where supported by the model:** In recurrent networks such as a Hopfield network, neuron states may be updated repeatedly until the network reaches a stable state.
6. **Output:** The retrieved pattern is returned.

### Example
Suppose a network stores the association between the pattern representing a particular letter and that complete letter pattern. If a damaged or incomplete version is presented, the network can use the stored association to retrieve the corresponding pattern, depending on the network design and its stored patterns.

### Types
- **Auto-associative memory:** Associates an input pattern with itself, helping reconstruct a stored pattern.
- **Hetero-associative memory:** Associates an input pattern with a different output pattern.

### Conclusion
Associative memory enables retrieval by association rather than requiring the input to be an exact copy of the stored pattern.

**Reference Deep Dive — Associative Memory:** The uploaded syllabus names auto-associative and hetero-associative memory, BAM and Hopfield networks under Module 5. The question bank does not specify a required numerical example, so the example above is illustrative.

## Q15. Analyze associative memory by examining its working mechanism and illustrating it with a suitable example. (7 marks)

**Ideal Answer**

### Definition
Associative memory is a neural-network approach in which a presented pattern is used to retrieve a related pattern stored in the network.

### Working mechanism
1. **Pattern representation:** Represent the input and output patterns in a suitable form.
2. **Learning/storage:** Store the required pattern or input-output association in the network's weights.
3. **Input presentation:** Present a known, partial or noisy pattern.
4. **Network processing:** The input activates the network through its weighted connections.
5. **Pattern retrieval:** The network generates the stored pattern or its associated output.
6. **State updating:** In networks designed for iterative retrieval, such as Hopfield networks, states may be updated until a stable state is reached.
7. **Output:** The retrieved pattern is provided as the network's response.

### Example
A system stores a complete binary pattern representing a symbol. Later, a version of that pattern with some entries missing or incorrect is presented. The network attempts to retrieve the stored symbol from the partial or noisy input. Successful retrieval depends on the stored patterns and the network's design.

### Main forms
- **Auto-associative:** Input and retrieved pattern are intended to be the same.
- **Hetero-associative:** Input is associated with a different output pattern.

### Conclusion
Associative memory is useful when a system must recall a pattern from a related, partial or noisy cue.

**Exam note:** Q13 and Q15 overlap significantly. Learn the common working mechanism once, then adapt the emphasis to the wording: Q13 asks specifically about retrieval; Q15 asks for the broader concept and working mechanism.

## Q14. Analyze the architecture of a Hopfield neural network and examine how its interconnected neurons contribute to associative memory. (7 marks)

**Ideal Answer**

### Definition
A **Hopfield network** is a recurrent neural network used as an associative memory. Its interconnected neurons can store patterns as stable states of the network.

### Architecture
1. **Neurons:** The network contains a set of neurons whose states represent a pattern.
2. **Recurrent connections:** Neurons are connected to other neurons, allowing the network's state to influence subsequent updates.
3. **Connection weights:** Weights encode information about the stored patterns.
4. **Feedback:** Unlike a feedforward network, signals can circulate through recurrent connections.
5. **State updating:** Neuron states are updated according to the network's activation/update rule.
6. **Energy function:** A Hopfield network is commonly described using an energy function. Under the usual conditions for the standard model and update rule, updates move the network toward a stable state.

### Role in associative memory
1. A complete or corrupted version of a stored pattern is presented as the initial state.
2. The interconnected neurons process the current state through their weighted connections.
3. Neuron states are updated.
4. The network continues updating until it reaches a stable state or attractor.
5. If the input lies within the retrieval region of a stored pattern, the stable state may correspond to that pattern.

### Advantages
- Can retrieve stored patterns from partial or noisy cues.
- Recurrent connections allow the network to settle into a stable state.
- Provides a model of content-addressable memory.

### Conclusion
The recurrent architecture, stored connection weights and stable states enable a Hopfield network to perform associative retrieval.

**Reference Deep Dive — Hopfield Network:** This answer expands the syllabus topic. The exact assumptions and update rule matter when proving convergence; they should not be omitted in a mathematical derivation.

## Q16. Compare BAM and hetero-associative memory based on architecture, working mechanism, input-output relationship, and applications. (7 marks)

**Ideal Answer**

### Introduction
Hetero-associative memory stores associations between an input pattern and a different output pattern. **Bidirectional Associative Memory (BAM)** is a bidirectional associative-memory model that can retrieve associated patterns in either direction.

| Basis | Hetero-associative memory (general) | Bidirectional Associative Memory (BAM) |
|---|---|---|
| Meaning | Associates one pattern with a different pattern. | A hetero-associative model designed for bidirectional recall. |
| Architecture | Uses connections that map input patterns to associated output patterns; architecture depends on the model. | Uses two neuron layers connected by weighted links, with recall possible in both directions. |
| Working | Input activates the network to produce its associated output. | An input pattern in either layer produces an associated pattern in the other layer; alternating updates may be used. |
| Input-output relationship | Typically described as input pattern → associated output pattern. | Supports A → B and B → A recall. |
| Direction | May be one-directional, depending on implementation. | Bidirectional by design. |
| Applications | Pattern association, paired-pattern retrieval and mapping one representation to another. | Bidirectional recall between paired patterns and associative pattern retrieval. |

### Working of BAM
1. Patterns are stored as associated pairs.
2. A pattern is presented to one of the two layers.
3. Weighted connections activate the other layer.
4. The resulting pattern can be fed back in the reverse direction.
5. The process may continue until the pair becomes stable.

### Conclusion
BAM is a particular form of hetero-associative memory that emphasizes recall in both directions. Hetero-associative memory is the broader category.

**Reference Deep Dive — BAM:** This comparison uses the standard conceptual distinction. Specific BAM weight-learning equations were not requested in this question.

---

# PRIORITY 2 — MODULE 6: 7-MARK THEORY

## Q22. Analyze the process of fuzzification and compare the different defuzzification techniques used in a fuzzy inference system. (7 marks)

**Ideal Answer**

### 1. Fuzzification
**Fuzzification** converts a crisp numerical input into degrees of membership in one or more fuzzy sets using membership functions. A membership degree generally lies between 0 and 1.

For example, a temperature input may have partial membership in the fuzzy sets *Warm* and *Hot* rather than belonging exclusively to one category.

### 2. Role in a fuzzy inference system
1. Receive crisp input values.
2. Use membership functions to determine membership degrees.
3. Apply fuzzy rules to the fuzzified inputs.
4. Combine the rule outputs to obtain an aggregated fuzzy output.
5. Apply defuzzification to obtain a crisp output when required.

### 3. Defuzzification
**Defuzzification** converts the aggregated fuzzy output into a single crisp value suitable for decision-making or control.

### 4. Defuzzification techniques

| Technique | Principle | Key characteristic |
|---|---|---|
| Centre of Gravity (COG/Centroid) | Finds the centre of area of the aggregated output membership function. | Uses the overall shape of the output set. |
| Mean of Maximum (MoM) | Calculates the mean of all output values having the maximum membership degree. | Averages the locations of maximum membership. |
| Smallest of Maximum (SoM) | Selects the smallest output value at which the maximum membership degree occurs. | Chooses the leftmost maximum. |
| Largest of Maximum (LoM) | Selects the largest output value at which the maximum membership degree occurs. | Chooses the rightmost maximum. |

For a discrete universe, the centroid can be represented as:

\[
z^* = \frac{\sum_i z_i\mu(z_i)}{\sum_i \mu(z_i)}
\]

where \(z_i\) is an output value and \(\mu(z_i)\) is its aggregated membership degree. For a continuous universe, the corresponding expression uses integrals.

### 5. Comparison
- **Centroid:** Considers the overall aggregated membership distribution, but may require more computation.
- **MoM:** Averages all values that attain the maximum membership.
- **SoM:** Selects the smallest value among the maxima.
- **LoM:** Selects the largest value among the maxima.

### Conclusion
Fuzzification represents crisp inputs using fuzzy membership, fuzzy inference applies rules, and defuzzification converts the final fuzzy result into a crisp value. The appropriate defuzzification technique depends on the required output and system design.

**Reference Deep Dive — Fuzzy Inference:** The listed techniques match the uploaded syllabus. The syllabus names the methods but does not provide their detailed derivations.

## Q21. Analyze the different activation functions used in ANN and compare their characteristics and applications, with reference to unipolar and bipolar functions. (7 marks)

**Ideal Answer**

### Definition
An activation function determines a neuron's output from its net input. It introduces non-linearity where the selected function is non-linear, allowing a network to learn more complex relationships.

### 1. Unipolar step activation function
The unipolar step function produces either 0 or 1.

\[
f(x)=
\begin{cases}
1, & x \geq 0\\
0, & x < 0
\end{cases}
\]

**Characteristics**
- Output range: 0 to 1.
- Does not produce negative outputs.
- Simple and computationally inexpensive.
- Discontinuous at the threshold and not differentiable there.

**Applications:** Simple threshold-based decisions and early perceptron-style models.

### 2. Bipolar step activation function
The bipolar step function produces either −1 or +1.

\[
f(x)=
\begin{cases}
1, & x \geq 0\\
-1, & x < 0
\end{cases}
\]

**Characteristics**
- Output range: −1 to +1.
- Produces both positive and negative outputs.
- Has a symmetric output range around zero.
- Is a step function and is not suitable for ordinary gradient-based learning at its discontinuity.

**Applications:** Simple threshold-based models where two classes or states are represented by −1 and +1.

### 3. Comparison

| Feature | Unipolar step | Bipolar step |
|---|---|---|
| Output values | 0 and 1 | −1 and +1 |
| Output range | 0 to 1 | −1 to +1 |
| Negative output | No | Yes |
| Symmetry around zero | No | Yes |
| Computation | Simple | Simple |
| Differentiability at threshold | Not differentiable | Not differentiable |
| Typical use | Binary threshold output | Two-state output represented with opposite signs |

### 4. Other common activation functions
Depending on the ANN architecture, other functions include:
- **Sigmoid:** Produces a smooth output between 0 and 1.
- **Hyperbolic tangent (tanh):** Produces a smooth output between −1 and +1.

These differ from step functions because they are continuous; their derivatives can be used in gradient-based learning.

### Conclusion
Unipolar and bipolar step functions are simple threshold functions with different output ranges. The choice depends on the output representation and learning method. Step functions are generally unsuitable for gradient-based training because of their discontinuity and lack of a useful derivative at the threshold.

**Source alignment:** The college notes explicitly cover unipolar and bipolar step functions. Sigmoid and tanh are included as brief additional context; the question specifically emphasizes unipolar and bipolar functions.

---

# PRIORITY 3 — MODULE 4: 2-MARK THEORY

## Q2. List the major components of an artificial neuron. (2 marks)

**Ideal Answer**

The major components of an artificial neuron are:
1. Inputs
2. Weights
3. Bias
4. Summation unit
5. Activation function
6. Output

The summation unit calculates the weighted sum of inputs, adding bias where used. The activation function determines the final output. *(Based on the college notes.)*

## Q3. What is meant by an activation function? (2 marks)

**Ideal Answer**

An activation function determines a neuron's output based on its net input. It can introduce non-linearity, enabling an ANN to learn complex relationships. Examples in the college notes are unipolar and bipolar step functions.

## Q4. Why are activation functions required in neural networks? (2 marks)

**Ideal Answer**

Activation functions introduce non-linearity into neural networks. Without non-linear activation functions, stacked layers of ordinary linear transformations would still represent a linear transformation, limiting the network's ability to learn complex relationships.

## Q1. Explain the concept of Artificial Neural Network (ANN) and its basic working. (2 marks)

**Ideal Answer**

An Artificial Neural Network (ANN) is a computing model inspired by the human brain. It consists of interconnected processing units called neurons and learns from examples through training.

**Working:** Inputs are multiplied by weights, the weighted values are summed with bias where used, an activation function is applied, and the neuron produces an output.

**Flow:** Input → Weighted Sum → Activation Function → Output.

---

# PRIORITY 4 — MODULE 5: 2-MARK THEORY

## Q10. Explain hetero-associative memory with a suitable example. (2 marks)

**Ideal Answer**

**Hetero-associative memory** stores an association between an input pattern and a different output pattern. When the input pattern is presented, the network retrieves its associated output.

**Example:** A system stores a person's name associated with that person's identification code. Presenting the name retrieves the associated code.

## Q11. Explain the advantages of Bidirectional Associative Memory (BAM). (2 marks)

**Ideal Answer**

Advantages of BAM include:
1. It supports associative recall in both directions between paired patterns.
2. It can retrieve an associated pattern when a pattern from either layer is presented.
3. Its recurrent interaction supports iterative recall toward a stable association under the model's operating conditions.

## Q12. Explain the concept of the energy function in a Hopfield network. (2 marks)

**Ideal Answer**

The **energy function** is a scalar measure associated with the state of a Hopfield network. Under the standard network assumptions and update rule, neuron updates move the network toward lower-energy states. A stable state corresponds to a local minimum of the energy function and may represent a stored pattern.

## Q9. Explain the concept of an associative memory network. (2 marks)

**Ideal Answer**

An associative memory network is a neural network that stores patterns or associations and retrieves a related stored pattern when given a complete, partial or noisy cue. Auto-associative memory retrieves the same pattern, whereas hetero-associative memory retrieves a different associated pattern.

---

# PRIORITY 5 — MODULE 6: 2-MARK THEORY

## Q18. Explain the need for fuzzification in a fuzzy inference system. (2 marks)

**Ideal Answer**

Fuzzification converts crisp input values into membership degrees in relevant fuzzy sets. It allows a fuzzy inference system to represent vague concepts such as *low*, *medium* and *high*, and provides the membership values needed to evaluate fuzzy rules.

## Q17. Explain the concept of defuzzification in a fuzzy inference system. (2 marks)

**Ideal Answer**

Defuzzification converts the aggregated fuzzy output of a fuzzy inference system into a crisp numerical value. This value can be used for a final decision or control action. Common techniques include Centre of Gravity, Mean of Maximum, Smallest of Maximum and Largest of Maximum.

## Q19. Describe the steps involved in fuzzy reasoning. (2 marks)

**Ideal Answer**

The main steps in fuzzy reasoning are:
1. **Fuzzification:** Convert crisp inputs into membership degrees.
2. **Rule evaluation:** Evaluate the applicable IF–THEN fuzzy rules.
3. **Aggregation:** Combine the outputs of the evaluated rules.
4. **Defuzzification:** Convert the aggregated fuzzy output into a crisp value when required.

## Q20. Describe the relationship between fuzzy rules and fuzzy inference. (2 marks)

**Ideal Answer**

Fuzzy rules are IF–THEN statements that express relationships between fuzzy conditions and conclusions. Fuzzy inference is the process of applying these rules to fuzzified inputs, determining the rules' contributions and combining their outputs to produce a fuzzy result.

---

# FINAL PROGRESS TRACKER

## Separate numerical track
- [ ] Q5 — Unipolar step function
- [ ] Q6 — Bipolar activation function
- [ ] Q7 — Delta learning rule
- [ ] Q8 — Multiple outputs using binary sigmoid

**Important:** These are study-ready draft answers. Before final memorization, check any lecturer-specific definitions, diagrams or examples against the college's teaching material. Module 5 and Module 6 answers are reference-based expansions because the uploaded college notes supplied here focus on Module 4.
"""
