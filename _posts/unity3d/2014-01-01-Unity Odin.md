---
layout: post
title: Unity Odin
category: 编程开发
tags: unity3d
keywords: 
description: 
---

#### 序列化Dictionary,继承SerializedMonoBehaviour

#### Display As String Attribute

```

[InfoBox("Additionally, you can also configure the string's alignment, font size, and whether it should support rich text or not.")]
[DisplayAsString(false, 20, TextAlignment.Center, true)]
public string CustomFontSizeAlignmentAndRichText = "This string is <b><color=#FF5555><i>super</i> <size=24>big</size></color></b> and centered.";
```

#### List

```
[LabelText("特效额外信息")][ShowIf("ShowExtraDataList")] [ListDrawerSettings(ShowFoldout = true, HideAddButton = true, HideRemoveButton = true)]
[OdinSerialize]
public List<EffectExtraData> ExtraDataList = new List<EffectExtraData>();
```

## Reference

