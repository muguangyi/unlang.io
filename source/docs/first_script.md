---
title: First Script
---

> Let's print `Hello UNLang!` in Unity console window.

## ① Create "Hello UNLang!" Script

* Back to Unity editor, you will see `UNLang/IDE...` menu.
  ![unlang-1](/assets/unlang-1.png)
* Open the `IDE` window.
* Right click in the `IDE` window and you will see all operations in the context menu.
  ![unlang-2](/assets/unlang-2.png)
* Add `Entry`, `Constant` and `Console` modules, then connect them as following:
  ![unlang-3](/assets/unlang-3.png)
* Select `Constant` module and in the **Inspector** window, choose `String` type and input `Hello UNLang!`.
  ![unlang-4](/assets/unlang-4.png)
* Right click to save the script to local project, for example, `[UnityProject]/Assets/Resources/1.bytes`.
  ![unlang-5](/assets/unlang-5.png)

## ② Run the Script

* Create a GameObject in the active scene.
* Attach an empty MonoBehaviour cs file.
* Edit the empty MonoBehaviour cs file with the following code:
  
  ```csharp
  using UnityEngine;
  using UNLang;
  using UNode;

  public class NewBehaviourScript : MonoBehaviour
  {
      // UNLang instance to execute the script.
      private LangInstance instance = null;

      void Start()
      {
          // Take over the loader since we put the script file
          // under Resources folder.
          NodeLoader.Load = file =>
          {
              return Resources.Load<TextAsset>(file).bytes;
          };

          // Create UNLang instance.
          this.instance = new LangInstance();
          // Load script file "1.bytes".
          this.instance.Load("1");
          // Start the script from "Entry" module.
          this.instance.Run<Entry>();
      }

      void Update()
      {
          // Update UNLang instance.
          this.instance?.Update();
      }
  }
  ```

* Congrats with `Hello UNLang!` in Unity console window.
