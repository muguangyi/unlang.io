---
title: Loader
---

**UNLang** need to know where to load the script files. The default loader of UNLang is loading file in project folder with **System.IO.File** for Unity editor. But during the runtime, Unity has several asset files' locations, like `Resources`, `StreamingAssets` and `PersistentDataPath`. UNLang doesn't know how to load, so it exports a way to user to take over the loader operation.

## Override Default

Check the API definition first. And what user need to do is set `Load` delegate with customized method.

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

For example, your application is using `Resources` as the assets' folder, then you could use **UnityEngine.Resources** API to take over the default.

```csharp
UNode.NodeLoader.Load = file =>
{
    return UnityEngine.Resources.Load<TextAsset>(file).bytes;
}
```

And if your application is using `Asset Bundle` as the assets, you could use `AssetBundle` API to override the default as well.

> `NOTE`: Override loader should be before UNLang instance runs the script.
