<!-- solve-problem:a442d3b2-3a06-4f44-83d1-97e719687448 -->
# Černý conjecture

A [Tangle Solve problem](https://solve.tangle.tools/problems/a442d3b2-3a06-4f44-83d1-97e719687448).

## What is the problem?

A **deterministic finite automaton (DFA)** is a triple with state set Q (|Q| = n) and, for each letter a of a finite alphabet Σ, a map Q → Q. A word w ∈ Σ* is **synchronizing** if it maps all states to a single state: |Q·w| = 1. Not every DFA admits one; those that do are called **synchronizing** (equivalently, for every pair of states p, q there exists a word mapping p and q to the same state — the "pair automaton" / power automaton condition).

**Conjecture (Černý, 1964):** every synchronizing DFA on n states has a synchronizing word of length at most **(n−1)²**.

The bound is tight if true: the Černý automaton C_n (two letters; one is a cyclic permutation of Q, the other fixes all states except one) achieves exactly (n−1)². The problem asks to prove this upper bound or exhibit a counterexample (a DFA requiring a longer word). Note the conjecture concerns the *worst case* over all synchronizing n-state DFAs; the relevant quantity is the maximal length ℓ(n) of the shortest synchronizing word.

## Why does it matter?

The conjecture is arguably the central open problem in automata synchronization theory, with connections to symbolic dynamics, matrix semigroups, coding theory, and part orientation in robotics. A resolution — especially a counterexample — would reshape the field, since hundreds of papers assume or work around the (n−1)² barrier. Practically, synchronization governs reset sequences for systems with uncertain state (model-based testing, fault recovery, NFA determinization heuristics), where tighter length bounds mean shorter reset procedures.

## What's already known?

- **Best general upper bound:** cubic, roughly n³/6. The classic bound is (n³ − n)/6 (Frankl-Pin via a combinatorial theorem on pair contraction); the current best is n(7n² + 6n − 16)/16 (Szykuła, 2018), still cubic — a gap of order n versus (n−1)².
- **Confirmed cases:** the conjecture holds for DFAs with small alphabet (|Σ| ≤ 3 in various cases, e.g., aperiodic automata, slowly synchronizing classes), for orientable automata (Trahtman), for cyclic/monotonic automata, and for all n up to roughly 8–10 by exhaustive computer search (verify exact current limit).
- **Approaches tried:** greedy/pair-automaton arguments (give cubic), the "eat the states one at a time" strategy (gives 2ⁿ in general, better in structured classes), extensions of Frankl's set-pair theorem (source of the best bounds), algebraic/semigroup methods (wipeout sets, Černý-like families). All fall short because they lose a factor of ~n in accounting for how state pairs merge.
- Known infinite families achieving quadratic length exist (Wielandt, primality-based, Kari's and others'), but none exceed (n−1)².

## What would count as solving it?

1. **Proof:** a theorem showing every synchronizing n-state DFA has a reset word of length ≤ (n−1)². A referee would accept any rigorous argument, published in a standard venue.
2. **Disproof:** an explicit synchronizing DFA whose shortest reset word has length > (n−1)² (with computer verification of the shortest-word length), or a nonconstructive existence proof.
3. **Partial credit variants:** improving the general cubic upper bound to o(n³), or extending the confirmed range of n via exhaustive search with a published, verified method.

## How to start

1. Read Volkov's survey "Synchronizing automata and the Černý conjecture" — the definitive overview of the landscape, techniques, and confirmed cases.
2. Study the Frankl–Pin argument (compressing one pair at a time via the set-pair theorem) and Szykuła's improvement, to understand exactly where the cubic loss arises; any progress likely requires a smarter account of merging multiple pairs simultaneously.
3. Reproduce Trahtman's proof for orientable automata and the Černý automaton construction to calibrate.
4. Consider computational search: encode "shortest reset word length" via the power automaton and search for counterexamples among n = 9–12 states (previous searches up to ~10 states found none); this is tractable only with strong symmetry/pruning heuristics.

Main obstacle: known techniques bound the cost of merging pairs independently, incurring n³; beating (n−1)² seems to require exploiting global structure that no current method captures.

## Key references

- M. Volkov, "Synchronizing automata and the Černý conjecture," *LATA 2008, LNCS 5196*. Survey of the problem, techniques, and partial results. (No stable link; find via Springer.)
- J. Černý, "Poznámka k homogénnym experimentom s konečnými automatmi," *Mat.-fyz. čas. Slovensk. Akad. Vied* 14 (1964). Original statement of the conjecture and the extremal automata C_n.
- P. Frankl, "An extremal problem for two families of sets," *Eur. J. Comb.* 3 (1982). Set-pair theorem underlying the cubic bound (combined with Pin).
- M. Szykuła, "Improving the upper bound on the length of the shortest reset word," *STACS 2018*. Best known general bound n(7n²+6n−16)/16.
- M. Trahtman, "The Černý conjecture for aperiodic automata," *Discrete Math. Theor. Comput. Sci.* 9 (2007). Proves the quadratic bound for a broad structured class. (verify)
- Wikipedia, "Synchronizing word" / unsolved problems list — entry-level overview. https://en.wikipedia.org/wiki/Synchronizing_word

## Warnings

- The conjecture is over **DFAs**; for NFAs or partial automata the analogous questions differ and are mostly settled differently — don't conflate settings.
- "Synchronizing" requires the automaton be strongly connected only in derived claims; the definition needs only a single word mapping all states together. Verify total (everywhere-defined) transition functions.
- A near-universal failure mode: arguments that merge pairs one at a time can never beat cubic by known analysis — a genuinely new idea is needed.
- Exhaustive-search claims (e.g., "verified for n ≤ 10") should be independently checked before relying on them.

---
*`ALGO-000224` · unverified*

## Acceptance guidance

1. **Proof:** a theorem showing every synchronizing n-state DFA has a reset word of length ≤ (n−1)². A referee would accept any rigorous argument, published in a standard venue.
2. **Disproof:** an explicit synchronizing DFA whose shortest reset word has length > (n−1)² (with computer verification of the shortest-word length), or a nonconstructive existence proof.
3. **Partial credit variants:** improving the general cubic upper bound to o(n³), or extending the confirmed range of n via exhaustive search with a published, verified method.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/a442d3b2-3a06-4f44-83d1-97e719687448?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000224.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000224)
