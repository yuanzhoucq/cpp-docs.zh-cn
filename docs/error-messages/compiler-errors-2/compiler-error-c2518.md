---
title: 编译器错误 C2518
ms.date: 11/04/2016
f1_keywords:
- C2518
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
ms.openlocfilehash: 315edc3124b4cdd425ce9d7581167366d3831512
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214641"
---
# <a name="compiler-error-c2518"></a>编译器错误 C2518

关键字 "关键字" 在基类列表中非法;掉

关键字 **`class`** 和 **`struct`** 不应出现在基类列表中。

下面的示例生成 C2518：

```cpp
// C2518.cpp
// compile with: /c
class B {};
class C : public class B {};   // C2518
class D: public B {};   // OK
```
