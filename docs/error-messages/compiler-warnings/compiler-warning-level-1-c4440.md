---
title: 编译器警告（等级 1）C4440
ms.date: 11/04/2016
f1_keywords:
- C4440
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
ms.openlocfilehash: dbb10a83e619af04334af268381b2286b037257a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186772"
---
# <a name="compiler-warning-level-1-c4440"></a>编译器警告（等级 1）C4440

忽略从 "calling_convention1" 到 "calling_convention2" 的调用约定重定义

已忽略更改调用约定的尝试。

下面的示例生成 C4440：

```cpp
// C4440.cpp
// compile with: /W1 /LD /clr
typedef void __clrcall F();
typedef F __cdecl *PFV;   // C4440
```
