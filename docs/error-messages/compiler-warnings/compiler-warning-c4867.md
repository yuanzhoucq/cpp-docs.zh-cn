---
title: 编译器警告 C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: a2298f5369ff941a9d5ac38838f531d6db478739
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165088"
---
# <a name="compiler-warning-c4867"></a>编译器警告 C4867

"function"：函数调用缺少参数列表;使用 "call" 创建指向成员的指针

指向成员函数的指针初始化不正确。

此警告可能是由于对 Visual Studio 2005 执行的编译器一致性工作引起的：增强了指针到成员的符合性。  在 Visual Studio 2005 之前编译的代码现在将生成 C4867。

此警告总是作为错误发出。 请使用 [警告](../../preprocessor/warning.md) 杂注禁用此警告。 有关 C4867 和 MFC/ATL 的详细信息，请参阅[_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)。

## <a name="example"></a>示例

下面的示例生成 C4867。

```cpp
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
