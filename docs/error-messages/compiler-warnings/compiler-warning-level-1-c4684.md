---
title: 编译器警告（等级1） C4684
ms.date: 11/04/2016
f1_keywords:
- C4684
helpviewer_keywords:
- C4684
ms.assetid: e95f1a83-2784-4b05-ae94-12148e056e26
ms.openlocfilehash: f6ce86cc297a6529d58573f3e7d906f51771013b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052522"
---
# <a name="compiler-warning-level-1-c4684"></a>编译器警告（等级1） C4684

"attribute"： WARNING！！ 特性可能导致生成无效代码：小心使用

你使用了一个不应经常使用的属性。

下面的示例生成 C4684：

```cpp
// C4684.cpp
// compile with: /W1 /LD
[module(name="xx")]; // C4684 expected
[no_injected_text];
```