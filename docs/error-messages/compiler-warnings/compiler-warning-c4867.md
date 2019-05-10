---
title: 编译器警告 C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: 0fd5de46f713aed08508f8755c9e54c3ff46366b
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447201"
---
# <a name="compiler-warning-c4867"></a>编译器警告 C4867

function： 函数调用缺少参数列表;使用调用创建指向成员的指针

指向成员函数的未正确初始化。

为 Visual Studio 2005 执行的编译器一致性工作可以生成此警告： 增强的指针到成员一致性。  在 Visual Studio 2005 之前已编译的代码现在将生成 C4867。

始终作为错误发出此警告。 请使用 [警告](../../preprocessor/warning.md) 杂注禁用此警告。 有关 C4867 和 MFC/ATL 的详细信息，请参阅[_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)。

## <a name="example"></a>示例

下面的示例生成 C4867。

```
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```