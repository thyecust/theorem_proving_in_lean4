Chinese Translation 中文翻译:

- [ ] [引论 Introduction](./introduction_zh.md)
- [ ] [依值类型论 Dependent Type Theory](./dependent_type_theory_zh.md)
- [ ] [命题和证明 Propositions and Proofs](./propositions_and_proofs_zh.md)
- [ ] [量词和相等 Quantifiers and Equality](./quantifiers_and_equality_zh.md)
- [ ] [Tactics](./tactics_zh.md)
- [ ] [与Lean交互 Interacting with Lean](./interacting_with_lean_zh.md)
- [ ] [归纳类型 Inductive Types](./inductive_types_zh.md)
- [ ] [归纳与递归 Induction and Recursion](./induction_and_recursion_zh.md)
- [ ] [结构与记录 Structures and Records](./structures_and_records_zh.md)
- [ ] [类型类 Type Classes](./type_classes_zh.md)
- [ ] [The Conversion Tactic Mode](./conv_zh.md)
- [ ] [公理与计算 Axioms and Computation](./axioms_and_computation_zh.md)

Theorem Proving in Lean 4
-----------------------

This manual is generated by [mdBook](https://github.com/rust-lang/mdBook). We are currently using a
[fork](https://github.com/leanprover/mdBook) of it for the following additional features:

* Add support for hiding lines in other languages [#1339](https://github.com/rust-lang/mdBook/pull/1339)
* Replace calling `rustdoc --test` from `mdbook test` with `./test`

To build this manual, first install the fork via
```bash
cargo install --git https://github.com/leanprover/mdBook mdbook
```
Then use e.g. [`mdbook watch`](https://rust-lang.github.io/mdBook/cli/watch.html) in the root folder:
```bash
mdbook watch --open  # opens the output in `out/` in your default browser
```

Run `mdbook test` to test all `lean` code blocks.

## How to deploy

```
./deploy.sh
```
