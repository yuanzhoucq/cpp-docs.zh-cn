---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 29f57eac7201ac0647275c70c539f9b2f28eb81b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179245"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>语法

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>备注

**Protected**关键字指定对*成员列表*中的类成员的访问，直到下一个访问说明符（**public**或**private**）或类定义的末尾。 声明为**protected**的类成员仅可用于以下项：

- 最初声明这些成员的类的成员函数。

- 最初声明这些成员的类的友元。

- 使用公共或受保护访问（派生自最初声明这些成员的类）派生的类。

- 也对受保护成员具有专用访问权限的以私有方式派生的直接类。

在基类的名称前面时， **protected**关键字指定基类的公共成员和受保护成员都是其派生类的受保护成员。

受保护成员不像**私有**成员那样是私有成员，它们只能由声明它们的类的成员访问，但它们不像**公共**成员那样公开，它们在任何函数中都是可访问的。

派生类的任何友元或成员函数都可以访问同时声明为**static**的受保护成员。 未声明为**静态**的受保护成员仅可通过指向派生类的指针、引用或对象访问派生类中的成员函数。

相关信息，请参阅[控制对类成员的访问](member-access-control-cpp.md)中的[friend](../cpp/friend-cpp.md)、 [public](../cpp/public-cpp.md)、 [private](../cpp/private-cpp.md)和成员访问表。

## <a name="clr-specific"></a>/clr 专用

在 CLR 类型中， C++访问说明符关键字（**public**、 **private**和**protected**）会影响程序集的类型和方法的可见性。 有关详细信息，请参阅[成员访问控制](member-access-control-cpp.md)。

> [!NOTE]
>  使用[/LN](../build/reference/ln-create-msil-module.md)编译的文件不受此行为的影响。 在这种情况下，所有托管类（公共或私有）都将可见。

## <a name="end-clr-specific"></a>END /clr 专用

## <a name="example"></a>示例

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>另请参阅

[控制对类成员的访问](member-access-control-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
