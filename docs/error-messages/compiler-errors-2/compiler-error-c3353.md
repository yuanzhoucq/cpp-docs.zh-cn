---
title: 编译器错误 C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: 332e0b253aed53f2adadf448b6a9c0681abc825e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747444"
---
# <a name="compiler-error-c3353"></a>编译器错误 C3353

“delegate”: 委托只能从全局函数或者托管或 WinRT 类型的成员函数中创建

用[委托](../../extensions/delegate-cpp-component-extensions.md)关键字声明的委托只能在全局范围内声明。

以下示例生成 C3353：

```cpp
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```
