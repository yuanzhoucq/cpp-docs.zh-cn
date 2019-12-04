---
title: 编译器错误 C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: d47d99962d089d873cb9bbdf9baac7eab706fc16
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746885"
---
# <a name="compiler-error-c2504"></a>编译器错误 C2504

"class"：未定义基类

声明基类，但从未定义过。  可能的原因：

1. 缺少包含文件。

1. 外部基类未通过[extern](../../cpp/using-extern-to-specify-linkage.md)声明。

下面的示例生成 C2504：

```cpp
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

还行

```
class C{};
class D : public C {};
```
