---
title: 运行时
---

**UNLang 实例**（`LangInstance`）是运行UNLang脚本的容器。是使用者建立UNLang运行时的第一个对象。

## 建立运行时

在一个MonoBehaviour中，使用者可以使用`LangInstance`很容易建立**UNLang**运行时。

```csharp
private LangInstance instance = null;

void Start()
{
    // 创建UNLang实例。
    this.instance = new LangInstance();
    ...
}

void Update()
{
    // 每一帧更新UNLang实例。
    this.instance?.Update();
}

void OnDestroy()
{
    // 销毁UNLang实例。
    this.instance.Dispose();
    this.instance = null;
}
```

是不是很简单？
