 

**The big lesson: Lean says yes to the statement as written, not to the file's title.**

1. **A pass is not a proof of the title.** `∃ m, bilateralStep n = m` passes for any function at all, because you can just pick m to be the answer. Lean would accept it, but it says nothing about Collatz. That's why every file gets two labels: what Lean did (PASS, FAIL, and so on) and what the pass proves (PROVES-CLAIM, TRIVIAL, WEAK, and so on).
2. **Examples are not "for every n."** `runOsc 20 7 = 1` shows that one number, 7, reaches 1. Collatz needs a statement over all n. The doc labels this SPOT-CHECK.
3. **An open question goes in a `def`.** `EveryOrbitEventuallyPeriodic` is written as a definition, so it states the question without claiming it's proved. A file with `sorry` in it is never a clean PASS. It gets PASS-WARN, and you name the unfinished theorem.

**Small traps the doc found (from reading, confirm in the editor):**

- A `;` after an inner `by` keeps the next tactic inside that block. In `have h : P := by omega; simp [h]`, the `simp` runs after `omega` already finished, so Lean should say "no goals."
- Comment markers come in pairs, `/-` and `-/`. MathLabHodge has an extra closer on line 77, which should be a parse error.
- Copying from a phone can shift the indentation line by line. Lean cares about that in tactic blocks, so keep your original paste too.
- Compare files by hash before debating versions. Three Fluid Hodge files are identical, and two Bilateral files differ only in indentation.

**One claim I could not confirm.** The doc says `Mathlib.Data.Real.Basic` is now a deprecated shim and the real file is `Mathlib.Basic.Real.Basic`. My search found no sign of that name. The official docs index still lists `Mathlib.Data.Real.Basic` as the real-numbers file, though that may be an older snapshot. Let the Lean editor's own error settle it, and record the Mathlib version shown on screen.

**Where it stands:** every file is NOT RUN. The doc's run order starts with `rebilatral_colatz`, the best chance of a clean pass, at live.lean-lang.org, which works on a phone browser. If you paste me what Lean says after that run, I'll fill in the entry template for it.

Sources:
- [Mathlib docs: Real numbers from Cauchy sequences (Mathlib.Data.Real.Basic)](https://leanprover-community.github.io/mathlib4_docs/Mathlib/Data/Real/Basic)