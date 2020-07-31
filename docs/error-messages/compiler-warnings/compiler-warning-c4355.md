---
title: 编译器警告 C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: 2725db0e37f8e60f37ec1b534306f516fe10be33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223338"
---
# <a name="compiler-warning-c4355"></a>编译器警告 C4355

“this”: 用于基成员初始值设定项列表

**`this`** 指针仅在非静态成员函数中有效。 它不能用于基类的初始化表达式列表中。

基类构造函数和类成员构造函数在 **`this`** 构造函数之前调用。 实际上，已将指向未构造对象的指针传递到另一个构造函数。 如果这些其他构造函数访问任何成员或调用此上的成员函数，则结果将不确定。 在 **`this`** 所有构造完成之前，不应使用指针。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

下面的示例生成 C4355：

```cpp
// C4355.cpp
// compile with: /w14355 /c
#include <tchar.h>

class CDerived;
class CBase {
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function() = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase {
public:
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor
   virtual void function() {};
};

CBase::~CBase() {
   m_pDerived -> function();
}

int main() {
   CDerived myDerived;
}
```
