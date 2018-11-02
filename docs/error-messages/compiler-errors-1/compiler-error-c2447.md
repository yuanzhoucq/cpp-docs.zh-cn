---
title: 编译器错误 C2447
ms.date: 11/04/2016
f1_keywords:
- C2447
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
ms.openlocfilehash: 64dca8313af8b640b7b03c1ab27a1a31fa90de09
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638524"
---
# <a name="compiler-error-c2447"></a>编译器错误 C2447

“{”: 缺少函数标题(是否是老式的形式表？)

此编译器在全局范围内遇到了意外的左大括号。 大多数情况下，这是由格式错误的函数头、放错位置的声明或孤立的分号导致的。 若要解决此问题，请确认左大括号跟在格式正确的函数头后面，并且其前面没有声明或孤立的分号。

此错误也可能由旧式 C 语言形参列表引起。 若要解决此问题，请重构参数列表以使用现代样式（即括在括号中）。

下面的示例生成 C2447:

```
// C2447.cpp
int c;
{}       // C2447
```