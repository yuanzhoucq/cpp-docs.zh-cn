---
title: 编译器警告 C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: 9fa9b382b42a2fb8ba72fd9744c612af5dd598d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526787"
---
# <a name="compiler-warning-c4867"></a>编译器警告 C4867

function： 函数调用缺少参数列表;使用调用创建指向成员的指针

指向成员函数的未正确初始化。

为 Visual c + + 2005年执行的编译器一致性工作可以生成此警告： 增强的指针到成员一致性。  使用 Visual c + + 2005年之前已编译的代码现在将生成 C4867。

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