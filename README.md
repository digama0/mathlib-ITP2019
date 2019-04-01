# Formal theory for "Formalizing computability theory via partial recursive functions"

This repository contains the formal text corresponding to the paper [Formalizing computability theory via partial recursive functions](main.pdf) ([arXiv](https://arxiv.org/abs/1810.08380)) by M. Carneiro. It is based on commit [`c91e6c2`](https://github.com/leanprover-community/mathlib/commit/c91e6c2eb882b0fea4f4bdbba2b1c498cdf40da1) of [`leanprover-community/mathlib`](https://github.com/leanprover-community/mathlib).

* Section 2: Encodable sets
  * The `mkpair` function and properties are defined in [`data.nat.pairing`](src/data/nat/pairing.lean#L14-L15)
  * `encodable` is found at [`data.equiv.encodable`](src/data/equiv/encodable.lean#L16-L17)
  * `denumerable` is found at [`data.equiv.denumerable`](src/data/equiv/denumerable.lean#L16-L17)
  * with some additional instances at [`data.equiv.list`](src/data/equiv/list.lean)
* Section 3: Primitive recursive functions
  * Most of the rest of the paper is located in the [`computability`](src/computability/) folder, and this section is all located in [`computability.primrec`](src/computability/primrec.lean).
  * The definition in the first code block is [`nat.primrec`](src/computability/primrec.lean#L39-L47)
  * [`primcodable`](src/computability/primrec.lean#L105-L106)
  * [`primrec`](src/computability/primrec.lean#L144-L145) on arbitrary types
  * [`nat_strong_rec`](src/computability/primrec.lean#L979-L981)
  * [`list α` is primcodable](src/computability/primrec.lean#L802)
  * Section 3.1 concerns the "textbook definition" [`nat.primrec'`](src/computability/primrec.lean#L1132-L1141) and its [equivalence to `nat.primrec`](src/computability/primrec.lean#L1315)
* Section 4: Partial recursive functions
  * Section 4.1 talks about a type called `part α`, but here we have renamed a few things for the paper.
    * In the formal text it is actually called [`roption α`](src/data/pfun.lean#L11-L13) located in [`data.pfun`](src/data/pfun.lean)
    * The `pure` function is called [`some`](src/data/pfun.lean#L59)
    * The definition of the [`bind`](src/data/pfun.lean#L170-L171) factors through another definition called [`assert`](src/data/pfun.lean#L165-L166)
    * The `⊥` element is called [`none`](src/data/pfun.lean#L53)
    * The type of partial functions is notated `α →. β`
    * [`pfun.fix`](src/data/pfun.lean#L416-L422) and its main theorem [`mem_fix_iff`](src/data/pfun.lean#L429-L430)
  * The rest of the section is in [`computability.partrec`](src/computability/partrec.lean).
  * [`nat.rfind`](src/computability/partrec.lean#L57-L58)
  * [`nat.partrec`](src/computability/partrec.lean#L137-L147)
  * [`partrec`](src/computability/partrec.lean#L213-L215) on arbitrary types
  * [`computable`](src/computability/partrec.lean#L220)
  * The `ifz` problem mentioned in the text explains why we have [`sum_cases_right`](src/computability/partrec.lean#L620-L623), which requires that one of the branches be computable while the other is partial.
* Section 5: Universality
  * Section 5.1: Codes for functions is in [`computability.partrec_code`](src/computability/partrec_code.lean).
    * [`nat.partrec.code`](src/computability/partrec_code.lean#L32-L40)
    * [`code.eval`](src/computability/partrec_code.lean#L476-L487)
    * [`encode code`](src/computability/partrec_code.lean#L57-L65)
    * [`const`](src/computability/partrec_code.lean#L48-L50), [`eval_const`](src/computability/partrec_code.lean#L491-L493), [`const_prim`](src/computability/partrec_code.lean#L500)
    * [`curry`](src/computability/partrec_code.lean#L54-L55), [`eval_curry`](src/computability/partrec_code.lean#L497-L498), [`curry_prim`](src/computability/partrec_code.lean#L505)
  * [`code.evaln`](src/computability/partrec_code.lean#L541-L560), called `evalₖ` in the text
  * [`fixed_point`](src/computability/partrec_code.lean#L889-L890) and [`fixed_point₂`](src/computability/partrec_code.lean#L909-L910)
  * The final applications are in [`computability.halting`](src/computability/halting.lean).
    * The resolution to the `ifz` problem are in theorems [`partrec.cond`](src/computability/halting.lean#L104-L106) and [`partrec.sum_cases`](src/computability/halting.lean#L114-L117), which no longer have to assume that one branch is total
    * [`merge`](src/computability/halting.lean#L89-L92)
    * [`computable_iff_re_compl_re`](src/computability/halting.lean#L203-L204)
    * [`rice`](src/computability/halting.lean#L165-L168) is the theorem stated in the paper; the classical analogue is [`rice₂`](src/computability/halting.lean#L181-L183)
    * [`halting_problem`](src/computability/halting.lean#L197)
* Section 6: Future Work (bonus)
  * This is unfinished work but if you like you can look at [`computability.turing_machine`](src/computability/turing_machine.lean) which contains some work on proving the equivalence of Turing machines with computable functions as defined here.
