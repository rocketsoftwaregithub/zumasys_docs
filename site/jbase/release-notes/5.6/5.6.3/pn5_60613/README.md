# PN5_60613

<PageHeader />

## Description

Case Independence: Code formatter not handling certain variables correctly

### Previous Release Behavior

Variables named **MM** and **ME** were treated as reserved words, subsequently causing programs to produce compilation errors.

### Current Release Behavior

**MM** and **ME** are not treated as reserved words and can be used as normal variables.

Back to [5.6.3 Release Notes](./../README.md)

<PageFooter />
