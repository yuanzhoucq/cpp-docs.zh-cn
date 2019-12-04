---
title: 编译器错误 C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 7ee7fb6e66ca9d5e09ad0eb445262c5f87d2060e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757067"
---
# <a name="compiler-error-c2491"></a>编译器错误 C2491

"identifier"：不允许使用 dllimport 函数的定义

可以将数据、静态数据成员和函数声明为 `dllimport`，但不能定义为 `dllimport`。

若要解决此问题，请从函数定义中 `__declspec(dllimport)` 删除说明符。

以下示例生成 C2491：

```cpp
// C2491.cpp
// compile with: /c
// function definition
void __declspec(dllimport) funcB() {}   // C2491

// function declaration
void __declspec(dllimport) funcB();   // OK
```
