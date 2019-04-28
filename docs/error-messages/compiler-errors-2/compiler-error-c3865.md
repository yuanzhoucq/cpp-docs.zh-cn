---
title: 编译器错误 C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 846657d3598e268d78ff3c39f2bfc901756ad370
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302015"
---
# <a name="compiler-error-c3865"></a>编译器错误 C3865

calling_convention： 只能在本机成员函数上使用

已全局函数的函数或托管的成员函数上使用的调用约定。 仅在本机 （非托管） 的成员函数上可用的调用约定。

有关详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。

下面的示例生成 C3865:

```
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```