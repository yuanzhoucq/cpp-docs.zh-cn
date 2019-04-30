---
title: 编译器错误 C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: c38642d7abd4f2fd50792c548c9a5521b2da10ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402640"
---
# <a name="compiler-error-c3353"></a>编译器错误 C3353

“delegate”: 委托只能从全局函数或者托管或 WinRT 类型的成员函数中创建

与声明的委托[委托](../../extensions/delegate-cpp-component-extensions.md)关键字，只能在全局范围内声明。

以下示例生成 C3353：

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```