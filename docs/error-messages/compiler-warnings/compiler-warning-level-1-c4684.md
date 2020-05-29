---
title: 编译器警告（等级 1）C4684
ms.date: 11/04/2016
f1_keywords:
- C4684
helpviewer_keywords:
- C4684
ms.assetid: e95f1a83-2784-4b05-ae94-12148e056e26
ms.openlocfilehash: 017d2ad9ac327e99bdd9afb0914d17946103771c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175449"
---
# <a name="compiler-warning-level-1-c4684"></a>编译器警告（等级 1）C4684

"attribute"： WARNING！！ 特性可能导致生成无效代码：小心使用

你使用了一个不应经常使用的属性。

下面的示例生成 C4684：

```cpp
// C4684.cpp
// compile with: /W1 /LD
[module(name="xx")]; // C4684 expected
[no_injected_text];
```
