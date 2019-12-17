---
title: Graph
---

**UNLang Graph** could package a UNLang script to an isolated module and be reused by other scripts. It's a high level reuse for UNLang to abstract UNLang script.

The key step user must do is connecting `In` and `Out` modules in UNLang script to define the input parameters and return values of the `Graph`.

## Input Value

A `Graph` should define the input values, then UNLang could understand the `Graph` entrance and know how to connect with other module. Just like input parameters of function.

> Use `UNLang/Graph/In` module.

## Return Value

A `Graph` also could define the output result if it has.

> Use `UNLang/Graph/Out` module.

## Example

Let's make a UNLang script to implement integer addition (a + b = c) feature of calculator.

### Create `add` Graph

#### ① Create "+" module

* Use `UNLang/Operator/+` module as follows.
  ![unlang-add](../assets/unlang-add.png)
* Set `+` module value type to `Integer` in the `Inspector` window.

#### ② Connect "In" and "Out" module

* Add `UNLang/Graph/In` and `UNLang/Graph/Out` modules.
* Set `In` and `Out` module value type to `Integer` in the `Inspector` window.
* Connect as follows.
  ![unlang-graph](../assets/unlang-graph.png)

#### ③ Save to `add.bytes`

### Use `add` Graph

* Import `add` graph by clicking `Graph...` menu and choose `add.bytes` file.
* Setup the script as follows: Two constant values and print to console.
* Use `Entry` module as the beginning.
  ![unlang-usegraph](../assets/unlang-usegraph.png)

## Summary

The `Graph` will hide all detail modules but only show `In` and `Out` pins of the script. So `Graph` is a good way to abstract a complex script and make it as a module to be reused by other script in UNLang.
