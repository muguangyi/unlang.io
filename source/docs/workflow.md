---
title: Workflow
---

In UNLang, the main workflow is:

* Setup UNLang runtime.
* Create extended UNLang modules if needed.
* Create/edit UNLang script by using the modules (Buildin or Extended) in UNLang editor.
* Load and run the entry script.
* Destroy when the application is terminated.

## Setup Runtime

Use UNLang Instance (LangInstance) to setup UNLang runtime in MonoBehaviour.

## Extend UNLang Modules

UNLang only provides some basic buildin modules, and it's not enough for user to implement all logic directly (UNLang doesn't want to either). More specific modules which just follow some rules need to be extended by user.

## Edit UNLang Script

All buildin and extended modules could be used in UNLang editor directly. Then user could compose the logic by connecting different modules with curve lines.

## Run UNLang Script

Load target entry script file and run the entry module.

## Destroy

Destroy UNLang runtime object when needed.
