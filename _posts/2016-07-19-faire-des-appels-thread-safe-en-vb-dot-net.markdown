---
layout: post
title: "Faire des appels thread-safe en vb.net"
date: 2016-07-19 11:05:54 +0200
author: jeremy
comments: true
categories:
---

* 1 - Ajouter cette fonction au bas du code :

```vb
  Public Sub InvokeIfRequired(ByVal method As Action)
    If Me.InvokeRequired = True Then '"Me" being the current form.
      Me.Invoke(Sub() InvokeIfRequired(method)) 'Invoke this method to make it thread-safe.
    Else
      method.Invoke() 'Execute the specified method.
    End If
  End Sub
  ```
<!--break-->

* 2 - Puis faire des appels :


```vb
  InvokeIfRequired(AddressOf HideWindow) 'Va appeller la fonction HideWindow
  InvokeIfRequired(Sub() Me.Visible = True) 'Va rendre la fenêtre visible
  InvokeIfRequired(Sub() Me.WindowState = FormWindowState.Normal) ' Va régler le paramètre Me.WindowState sur Normal
```
