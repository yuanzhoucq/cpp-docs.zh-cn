---
title: 编译器错误 C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: eb7b55f63e911f155c13e777e2e84ae7b587e9a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432664"
---
# <a name="compiler-error-c3353"></a>编译器错误 C3353

“delegate”: 委托只能从全局函数或者托管或 WinRT 类型的成员函数中创建

与声明的委托[委托](../../windows/delegate-cpp-component-extensions.md)关键字，只能在全局范围内声明。

以下示例生成 C3353：

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```