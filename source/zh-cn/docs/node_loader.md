---
title: Loader
---

**UNLang**需要知道如何装载脚本文件。UNLang默认的加载器是在Unity编辑器下使用**System.IO.File**在项目的目录下加载文件。但是在运行时，Unity有几种存放资源文件的地方，例如`Resources`，`StreamingAssets`和`PersistentDataPath`。UNLang并不知道如何加载，因此需要使用者接管加载操作。

## 重写默认方式

首先看一看API定义。使用者需要提供一个自定义方法来设置`Load`托管方法。

```csharp
namespace UNode
{
    public delegate byte[] Load(string target);

    public static class NodeLoader
    {
        public static Load Load { get; set; }
    }
}
```

例如，你的应用是使用`Resources`作为资源目录，那么你就可以使用**UnityEngine.Resources** API来接管默认操作。

```csharp
UNode.NodeLoader.Load = file =>
{
    return UnityEngine.Resources.Load<TextAsset>(file).bytes;
}
```

而如何你的应用使用`Asset Bundle`作为资源，你也可以使用`AssetBundle` API来重写默认值。

> `注意`: 重写加载器必须发生在UNLang实例运行脚本之前。
