*BEGIN: Context Document Header*

# CONTEXT DOCUMENT — Continuation

## Course

**Name:**
Machine Learning University — Mathematics

**Short marker:**
mlumath

**Lecture(s):**
Lecture 1 / Lab 1.3–1.4 area: linear algebra review, norms, dot products, embeddings, and matrix operations.

**Primary topic(s):**
Linear algebra review; vectors, matrices, tensors-as-arrays vs mathematical tensors; norms and dot products; embeddings for LLMs; one-hot encodings; matrix multiplication; covariance and contravariance; dual spaces; covectors; metric tensor; Dirac bra-ket notation as dual-space notation.

---

## Continuation Metadata

**Prepared at:**
1783251790_2026-07-05T07:43:10-0400

Generated via:

date +'%s_%Y-%m-%dT%H:%M:%S%z'

(Boston, MA time)

**Continued from chat:**
MLU math / ADHD coaching / JabberVec / covariance-contravariance discussion

**Also involving:**
- Anti-perfectionism lecture-note workflow
- JabberVec / letter-level embedding project idea
- Einstein notation preferences for ML equations
- Dirac notation, gamma matrices, and dual spaces
- Family/logistics context only insofar as it affected study flow

---

## Author / Source

**User (GitHub):**
@bballdave025

**User (ChatGPT):**
Dave / D Black

---

## Intent for This Context

This document lets Future Dave or a fresh ChatGPT session resume MLU Mathematics work after Lecture 1 without re-deriving the major conceptual breakthroughs from the chat. It preserves the lecture-note rhythm, key mathematical intuitions, notation decisions, project ideas, and the covariance/contravariance understanding that clicked during the session.

---

## Usage Instructions

- Treat this document as authoritative learning state.
- Continue with minimal re-derivation.
- Preserve notation preferences whenever practical.
- Preserve intuition before optimization.
- When translating MLU equations, prefer explaining the mathematical object before the implementation array shape.

*ENDOF: Context Document Header*

# LN_mlumath_2026-07-04_-_lec01_linear_algebra_review_w_contra_co_variance

## Immediate Resume State

Dave is working through Machine Learning University Mathematics, Lecture 1. The working method that emerged is **anti-perfectionism commentary notes**:

- Listen to the lecture, often at increased speed.
- Use voice dictation rather than swipe typing when possible.
- Capture what clicks, what feels wrong, and what questions arise.
- Avoid rewinding except for genuinely important concepts.
- Later, use uGTgtdD / lab-notebook passes to convert rough commentary into symbolic notes.

The train and other constrained environments work well for this because the natural time limit discourages perfectionism. Voice notes are acceptable even when ASR mangles terms; Future Dave can usually reconstruct intent.

The high-level study goal is not merely to finish MLU, but to use MLU math as a bridge between:

- physics notation,
- Einstein index notation,
- machine learning implementation,
- interpretability / learned representations,
- and small portfolio-style projects such as JabberVec and Latent Forge.

## Lecture 1 High-Level Coverage

Lecture 1 reviewed core linear algebra for ML:

- vectors and matrices,
- tensors in the ML sense,
- matrix operations,
- transpose and inverse,
- Hadamard product,
- matrix multiplication,
- norms,
- dot products,
- distances and similarities,
- embeddings,
- one-hot encodings,
- and matrix multiplication as a core operation in LLMs.

A recurring critique/clarification:

> ML courses often say vectors and matrices are “data structures.” That is implementation-useful, but mathematically incomplete. Vectors and matrices are mathematical objects that may be represented computationally as arrays.

Similarly:

> ML “tensors” are often just multidimensional arrays. Mathematical tensors are objects defined by their transformation laws.

This distinction should be preserved in future notes. It matters when translating between ML implementations and physics/geometric intuition.

## Anti-Perfectionism Note-Taking Discovery

A useful workflow emerged:

1. First-pass commentary: rough voice notes while lecture plays.
2. Timestamp breadcrumbs if needed.
3. Later symbolic pass: rewrite only the parts worth preserving.
4. Avoid treating polished notes as a prerequisite for continuing the course.

Important phrase:

> Anti-perfectionism note-taking is not lower quality. It is a workflow that lets the course continue.

This is especially important because Dave’s project instincts can convert “learning” into “build a perfect note system before learning.” For MLU, capture-first is preferred.

## Embeddings and One-Hot Encodings

Important distinctions from the lecture discussion:

### Encoding vs Embedding

Encoding answers:

> How do I represent this item so a computer/model can identify it?

Embedding answers:

> How do I represent this item so mathematical operations reflect useful learned relationships?

An embedding is a kind of encoding, but not every encoding is an embedding.

### One-Hot Representation

For vocabulary size \(V\):

- each token has a one-hot vector of length \(V\),
- stacking all such vectors gives a \(V \times V\) identity matrix,
- one-hot representations identify tokens but encode no similarity structure.

### Embedding Matrix Shape

Most ML libraries store an embedding table as:

\[
E \in \mathbb{R}^{V \times D},
\]

where each row is a token embedding.

Dave’s physics/Eintein-notation preference often favors the transposed conceptual object:

\[
\mathcal{E}^{i}{}_{w},
\]

where:

- \(i\) indexes embedding dimensions,
- \(w\) indexes vocabulary/token identity,
- each token’s embedding is naturally a column vector.

Implementation convention is not mathematical necessity. PyTorch row-major orientation is convenience; Einstein notation should track the actual contraction.

### Embedding Dimension

Typical embedding dimension \(D\) is much smaller than vocabulary size \(V\), even in modern LLMs. Example scale:

- \(V \sim 50{,}000\) to \(100{,}000\),
- \(D \sim 768\), \(1536\), \(4096\), etc.

Thus \(D < V\) is still typical.

However, \(D > V\) is possible and not mathematically forbidden, especially in toy or character-level models. Example:

- vocabulary = 26 lowercase letters,
- embedding dimension = 64.

This was one motivation for JabberVec.

### Rich vs Dense

“Dense” means most coordinates are nonzero.

“Rich” means the vector captures many useful learned relationships.

A dense vector can be uninformative; a sparse representation can still be rich. The lecture may use these terms closely, but they should be kept distinct.

### Cosine Similarity

Cosine similarity clicked as:

> a measure of directional similarity after magnitude has been normalized away.

Parallel vectors have cosine similarity \(1\), antiparallel vectors \(-1\), and orthogonal vectors \(0\). Antiparallel still has a strong directional relation; orthogonal indicates no directional relation under this measure.

## Norms, Dot Products, and \(L_p\) Questions

Lecture 1 reviewed norms and dot products.

Important notes/questions:

- Norms measure lengths.
- Distances are lengths of connecting vectors.
- Norms are nonnegative.
- Triangle inequality is essential for true norms.
- \(L_p\) for \(p < 1\) can be defined algebraically in some contexts but fails the triangle inequality, so it is not a true norm.
- \(L_1\) vs \(L_2\) intuition:
  - \(L_2\): “Dave in class says, ‘you quiet down’” — smooth/shrinking penalty.
  - \(L_1\): “Dave says, ‘you, you, and you get out’” — sparsifying penalty.

This metaphor should be refined later, but it captures the sparsity distinction.

## Matrix Multiplication and Linear Functionals

A matrix-vector product can be understood row-by-row:

- each row acts as a linear functional,
- each row eats the input vector and returns one scalar,
- those scalars become components of the output vector.

In index notation, for a linear map \(M\):

\[
y^i = M^i{}_{j} x^j.
\]

The lower index \(j\) is contracted with the input vector’s upper index. The upper index \(i\) remains as the output component.

This is likely to become a preferred way to understand ML layers:

- row vectors are not “vectors turned sideways,”
- rows naturally behave like covectors / linear functionals,
- a layer is a collection of measurement machines producing a new vector.

## Compressing Embedding Matrices

When ML material says “compress the embedding matrix,” interpret this primarily as mathematical compression/factorization, not JPEG/MP3-style bitstream compression.

A typical low-rank idea:

\[
E \approx AB,
\]

where

\[
A \in \mathbb{R}^{V \times k},
\quad
B \in \mathbb{R}^{k \times D},
\quad
k \ll D.
\]

Then the original large lookup/linear operation can be replaced by a smaller factorized representation.

This connects directly to a future JabberVec experiment:

> How much can the learned embedding matrix be compressed before nearest-neighbor structure or pseudo-word generation quality degrades?

## Nonlinear Activations

Key insight:

- Pure stacks of linear maps collapse into one linear map.
- Nonlinear activations prevent this collapse.
- Deep learning’s power comes from alternating linear maps and nonlinearities.

ReLU is surprisingly simple:

\[
\operatorname{ReLU}(x)=\max(0,x).
\]

The astonishing fact is that repeated coordinate changes plus simple nonlinear bends can model highly complex phenomena.

Important conceptual line:

> The extraordinary behavior emerges from composition, not from any one individual piece.

## Universal Approximation and Depth

The Universal Approximation Theorem says, roughly, that a sufficiently wide network with one hidden layer and suitable activation can approximate a large class of continuous functions on compact domains.

But this is an existence theorem, not an efficiency theorem.

Analogy:

- NAND gates are functionally complete.
- Any Boolean circuit can be built from NAND gates.
- That does not mean a NAND-only naive construction is efficient, compact, or practical.

Similarly:

- one hidden layer can approximate many functions,
- but deep networks can represent some functions exponentially more efficiently,
- and training feasibility depends on compute, data, initialization, residual connections, optimization, GPUs, etc.

Historical clarification:

- Minsky and Papert’s *Perceptrons* showed real limitations of single-layer perceptrons.
- The popular “they set AI back 20 years” story is oversimplified.
- Neural-network progress also needed compute, data, backprop, GPUs, better optimization, and engineering advances.

## Compute History Context

Deep learning became practical partly because of long-term investment in high-performance computing from:

- defense / military research,
- NASA and space programs,
- particle physics and national labs,
- weather and climate modeling,
- nuclear weapons stewardship,
- computational chemistry / molecular biology,
- oil and gas seismic imaging,
- graphics and gaming GPUs,
- hyperscale cloud computing.

Important memory anchor:

> Sky, a grad school friend, was excited that an Apple GPU / Iris-style driver might allow lattice gauge calculations because GPUs are optimized for parallel linear algebra.

This connects physics/HPC history with modern ML hardware.

## Main Conceptual Breakthrough: Vector vs Covector

The central breakthrough of the session was the distinction between vectors and covectors.

### Before the Click

Dave knew how to use covariance and contravariance rules from E&M, GR, particle physics, and national lab work, but did not have a satisfying deep intuition.

The confusing issue was that in orthonormal Cartesian coordinates:

\[
a_i = a^i.
\]

Thus expansion coefficients and dot-product projections appear to be the same thing for years.

### Core Clarification

A vector is a geometric object. Coordinates are a representation.

Contravariant components answer:

> How many basis vectors do I add to construct this vector?

Covectors answer:

> What measurement can be made of a vector?

A covector is not merely “the same vector with a lowered index.” It is a different mathematical species.

Important phrase:

> The covector associated with that vector.

This phrase clicked strongly. It avoids saying “the covector equals the vector.” The metric associates vectors with covectors; it does not identify them in a naïve sense.

## Contravariant Components

Given basis vectors \(\mathbf e_i\), write:

\[
\mathbf a = a^i \mathbf e_i.
\]

The components \(a^i\) are construction coefficients.

If the basis doubles:

\[
\mathbf e'_i = 2\mathbf e_i,
\]

then the components halve:

\[
{a'}^i = \frac{1}{2}a^i.
\]

This is contravariance: the components vary contrary to the basis scaling.

Dave’s “ruler” analogy:

- measuring in one-foot rulers vs two-foot rulers,
- the physical displacement stays the same,
- the number of rulers changes inversely.

Important notation convention:

- hats mean unit vectors,
- general basis vectors should not receive hats unless explicitly unit length.

Use:

\[
\hat{\mathbf e}_i
\]

for unit basis vectors, and

\[
\mathbf e'_i = 2\hat{\mathbf e}_i
\]

for a scaled non-unit basis vector.

## Covectors and Linear Functionals

A functional is:

> a function whose input is a vector and whose output is one scalar.

A linear functional is a functional that is linear.

The dual space \(V^*\) is:

\[
V^* = \{\text{all linear functionals on } V\}.
\]

A covector is an element of \(V^*\).

Important interpretation:

- vectors live in \(V\),
- covectors live in \(V^*\),
- covectors are “measurement machines,”
- a row vector naturally represents a covector because row times column gives a scalar.

Example:

\[
\begin{bmatrix}1 & 0\end{bmatrix}
\begin{bmatrix}2\\-6\end{bmatrix}
=2.
\]

The row vector acts as a machine that extracts one scalar from the column vector.

## Dual Basis

For basis vectors \(\mathbf e_j\), the dual basis \(\mathbf e^i\) is defined by:

\[
\mathbf e^i(\mathbf e_j)=\delta^i_j.
\]

If a metric/dot product is available, this can be represented as:

\[
\mathbf e^i\cdot \mathbf e_j=\delta^i_j.
\]

The dual basis restores projection intuition:

\[
a^i = \mathbf e^i(\mathbf a),
\]

or, with a Euclidean dot-product representation,

\[
a^i = \mathbf e^i \cdot \mathbf a.
\]

Important clarification:

- Dotting \(\mathbf a\) with the original basis vector \(\mathbf e_i\) gives covariant components:

\[
a_i = \mathbf a\cdot \mathbf e_i.
\]

- Dotting \(\mathbf a\) with the dual basis vector \(\mathbf e^i\) extracts contravariant components:

\[
a^i = \mathbf e^i\cdot \mathbf a.
\]

In an orthonormal basis, the basis and dual basis coincide, hiding the distinction.

## Metric Tensor

The metric tensor is written \(g_{\mu\nu}\) in GR and related contexts.

It lowers indices:

\[
v_\mu = g_{\mu\nu}v^\nu.
\]

This should be read as:

> Use the metric to construct the covector associated with the vector.

The inverse metric raises indices:

\[
v^\mu = g^{\mu\nu}v_\nu.
\]

The inverse metric is defined by:

\[
g^{\mu\alpha}g_{\alpha\nu}=\delta^\mu{}_{\nu}.
\]

Important clarification:

- \(g_{\mu\nu}\) is symmetric in GR:

\[
g_{\mu\nu}=g_{\nu\mu}.
\]

- Symmetric does not mean equal to its inverse.
- Hermitian conjugates are not generally the GR operation; GR is usually real-valued and uses transpose/symmetry rather than dagger.

For four-momentum:

\[
p_\mu = g_{\mu\nu}p^\nu.
\]

The invariant scalar is:

\[
p_\mu p^\mu,
\]

not \(p_\mu p^\nu\) with mismatched free indices.

## Dirac Bra-Ket Notation

A ket is a vector:

\[
|\psi\rangle \in V.
\]

A bra is a covector:

\[
\langle\psi| \in V^*.
\]

A bra is not merely “a ket turned sideways.” It lives in the dual space.

The relationship in Hilbert space is:

\[
\langle\psi| = (|\psi\rangle)^\dagger.
\]

The dagger means transpose plus complex conjugate.

If:

\[
|\psi\rangle =
\begin{bmatrix}
a\\b
\end{bmatrix},
\]

then:

\[
\langle\psi| =
\begin{bmatrix}
a^* & b^*
\end{bmatrix}.
\]

Expectation value:

\[
\langle\psi|\hat A|\psi\rangle
\]

should be read with evaluation order:

\[
\langle\psi|\left(\hat A|\psi\rangle\right).
\]

The operator acts on the ket first; then the bra evaluates the resulting ket.

Important wavefunction identity:

\[
\psi(x)=\langle x|\psi\rangle.
\]

Interpretation:

> The wavefunction is the representation of the abstract quantum state vector in the position basis.

For momentum in position representation:

\[
\hat p = -i\hbar\frac{\partial}{\partial x}.
\]

The expectation value in one dimension is:

\[
\langle\psi|\hat p|\psi\rangle
=\int \psi^*(x)\,\hat p\,\psi(x)\,dx.
\]

Here the \(\psi^*\) appears in the integral representation because the bra has become complex conjugation in the position basis. It is not written separately inside \(\langle\psi|\), because the bra already includes the dagger operation.

## Star vs Dagger

Important notation clarification:

- \(V^*\) means the dual space of \(V\).
- \(\psi^*\) means complex conjugate of \(\psi\).
- \(\dagger\) means adjoint / conjugate transpose.

The star in \(V^*\) is not complex conjugation; it names the dual space.

The dual space exists without an inner product or metric. The dagger requires additional structure, usually an inner product.

## Gamma Matrices and Slash Notation

Dirac gamma matrices are written:

\[
\gamma^\mu.
\]

Each \(\gamma^\mu\) is a \(4\times4\) matrix. The index \(\mu\) labels which gamma matrix, not a row or column.

If exposing hidden spinor indices:

\[
(\gamma^\mu)^a{}_{b}.
\]

There are multiple index systems:

- spacetime index \(\mu\),
- spinor row index \(a\),
- spinor column index \(b\).

Lowering the spacetime index:

\[
\gamma_\mu = g_{\mu\nu}\gamma^\nu.
\]

The metric changes only the spacetime index, not the internal matrix indices.

Feynman slash notation:

\[
\not{p}=\gamma^\mu p_\mu.
\]

The spacetime index is contracted, leaving a \(4\times4\) matrix/operator that can act on spinors.

## Differential Geometry Two-Minute Version

Differential geometry studies curved spaces by attaching a linear tangent space to each point.

Hierarchy:

1. Linear algebra: one vector space.
2. Tensor calculus: vectors, covectors, tensors, metrics inside a vector space.
3. Differential geometry: smoothly varying vector spaces attached to every point of a manifold.

General relativity says spacetime itself is the manifold, and gravity is encoded in how these tangent spaces fit together geometrically.

Important phrase:

> Vectors describe directions in which one can move. Covectors describe measurements that can be made of such directions. The metric associates vectors with covectors, but it does not identify them.

## Machine Learning Tensor Caution

ML tensors are often arrays, not necessarily mathematical tensors.

This is not because nonlinear activations destroy tensor-ness. It is because ML frameworks usually do not specify transformation laws under coordinate changes.

Even a purely linear PyTorch tensor is just an array unless it is assigned geometric transformation behavior.

However, Einstein notation is still useful for ML because it forces the question:

> What space does this index live in, and what contraction is being performed?

This should guide future MLU equation rewrites.

## JabberVec / Letter-Level Embedding Project

A side project was created/scaffolded as `jabbervec-l2v`, intended as a playful Letter2Vec / Lewis Carroll-inspired laboratory.

Core idea:

> Explore how English-like pseudo-words acquire structure through character-level embeddings.

Repo concept names considered:

- JabberVec
- JabberVec-l2v
- Letter2Vec Carroll
- Carroll2Vec
- LexiForge
- PhonoForge

Chosen direction: JabberVec / jabbervec-l2v.

Project framing:

> Looking through the embedding glass.

Playful hidden analogy:

> Like Feynman's path integrals, suppose every plausible English-looking word is allowed to exist. What geometry emerges?

Future experiments:

- train tiny character embeddings,
- visualize letter embeddings in 2D/3D,
- see whether vowels/consonants cluster,
- inspect whether `q` isolates due to `qu`,
- compare dictionary vs large corpus,
- generate pseudo-English words,
- perform PCA / dimensionality reduction,
- perform SVD / low-rank approximation,
- test when compression degrades neighborhood structure or generation quality,
- arbitrary mapping between real English words and same-length JabberVec words, then inspect clusters/projections.

## Favorite Phrases / Sentences to Preserve

1. Anti-perfectionism note-taking is not lower quality; it is a workflow that lets the course continue.

2. A vector is a geometric object; coordinates are one representation of that object.

3. Cartesian coordinates are so nice that they hide machinery that is still there.

4. Contravariant components answer: how many basis vectors do I add?

5. Covectors answer: what measurement can be made of a vector?

6. The row does not act like an arrow; it acts like a machine that eats arrows.

7. A linear functional is a machine that eats one vector and returns one scalar.

8. A bra is not a ket turned sideways; it lives in the dual space.

9. The metric associates a vector with a covector, but it does not identify them.

10. Lowering an index is constructing the covector associated with that vector.

11. The covector associated with that vector.

12. The dual basis restores the projection intuition.

13. The wavefunction is the representation of the abstract quantum state in the position basis.

14. The operator acts on the ket first; then the bra evaluates the resulting ket.

15. ML tensors are often just arrays unless transformation behavior is specified.

16. Einstein notation forces the question: what space does this index live in?

17. The extraordinary behavior of neural networks emerges from composition, not from any one piece.

18. Universal approximation is existence, not efficiency.

19. Dense describes the representation; rich describes what the representation contains.

20. Cosine similarity measures directional similarity after magnitude has been normalized away.

21. The embedding matrix is not the magic; it is the first learned representation that later layers refine.

22. The structure survives even when the representation changes.

23. JabberVec is not trying to compete with modern LLMs; it is trying to recreate the birth of the idea.

24. The goal is not just to use machine learning, but to understand learned representations deeply enough to make them simpler, more interpretable, or more controllable.

25. What I cannot create, I do not understand.

## Favorite Equations to Preserve

Contravariant expansion:

\[
\mathbf a = a^i\mathbf e_i.
\]

Basis scaling:

\[
\mathbf e'_i=2\mathbf e_i,
\qquad
{a'}^i=\frac12 a^i.
\]

Metric lowering:

\[
v_\mu = g_{\mu\nu}v^\nu.
\]

Metric raising:

\[
v^\mu = g^{\mu\nu}v_\nu.
\]

Inverse metric:

\[
g^{\mu\alpha}g_{\alpha\nu}=\delta^\mu{}_{\nu}.
\]

Momentum invariant:

\[
p_\mu p^\mu.
\]

Dual basis:

\[
\mathbf e^i(\mathbf e_j)=\delta^i_j.
\]

Contravariant component extraction:

\[
a^i=\mathbf e^i(\mathbf a).
\]

Bra from ket:

\[
\langle\psi|=(|\psi\rangle)^\dagger.
\]

Wavefunction as basis representation:

\[
\psi(x)=\langle x|\psi\rangle.
\]

Expectation value:

\[
\langle\psi|\hat A|\psi\rangle
=\langle\psi|\left(\hat A|\psi\rangle\right).
\]

Position-representation momentum operator:

\[
\hat p=-i\hbar\frac{\partial}{\partial x}.
\]

Gamma matrix with hidden spinor indices:

\[
(\gamma^\mu)^a{}_{b}.
\]

Lowered gamma:

\[
\gamma_\mu=g_{\mu\nu}\gamma^\nu.
\]

Slash notation:

\[
\not{p}=\gamma^\mu p_\mu.
\]

Embedding lookup in Dave-style orientation:

\[
x^i = \mathcal{E}^{i}{}_{w}\,t^w.
\]

Linear layer:

\[
y^i = M^i{}_{j}x^j + b^i.
\]

## Open Questions / Follow-Ups

1. Build a clean Einstein-notation guide for ML linear layers, embeddings, attention, and normalization.

2. Clarify tensor terminology in MLU notes: array vs mathematical tensor.

3. Revisit dual bases with an explicit 2D skew-basis diagram or numerical example.

4. Revisit covariance/contravariance with Faculty of Khan videos:
   - tensors intro: `uaQeXi4E7gA`
   - covariance/contravariance example: `vvE5w3iOtGs`
   - part 2: `BaIMIRmUtLs`

5. Revisit 3Blue1Brown / Khan / Dan Fleisch / Eugene Khutoryansky explanations for visual reinforcement.

6. Continue Lecture 1 knowledge check / quiz if not already completed.

7. Begin next MLU math lecture using anti-perfectionism voice commentary.

8. Create a polished but not over-polished notebook cell containing favorite phrases and equations from this document.

9. Use JabberVec as a future sandbox for embeddings, PCA, SVD, low-rank approximation, and pseudo-word generation.

10. Eventually generate a `README.md` for `courses_tutorials_etc/mlu/mlu-math/docs/context_docs/` based on the specialized mlumath README already drafted in chat.

## Immediate Next Steps

1. Save this file as:

```text
courses_tutorials_etc/mlu/mlu-math/docs/context_docs/LN_mlumath_2026-07-04_-_lec01_linear_algebra_review_w_contra_co_variance.md
```

2. Create or update:

```text
courses_tutorials_etc/mlu/mlu-math/docs/context_docs/README.md
```

using the `mlumath`-specific README drafted in this chat.

3. In the next MLU chat/session, begin with a PCDP or this context doc.

4. Continue MLU math lectures using the anti-perfectionism commentary method.

5. When equations appear, translate them into Einstein notation where doing so clarifies the contraction and spaces involved.

*End of Context Document*
