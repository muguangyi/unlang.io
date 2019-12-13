---
title: UNLang Runtime
---

**UNLang Instance** (`LangInstance`) is the container to run UNLang script. It's the first object user should use to setup UNLang runtime.

## Setup Runtime

In a MonoBehaviour, user could setup **UNLang** runtime with `LangInstance` easily.

```csharp
private LangInstance instance = null;

void Start()
{
    // Create UNLang instance.
    this.instance = new LangInstance();
    ...
}

void Update()
{
    // Update UNLang instance per frame.
    this.instance?.Update();
}

void OnDestroy()
{
    // Destroy UNLang instance.
    this.instance.Dispose();
    this.instance = null;
}
```

That's all. Is it simple enough?
