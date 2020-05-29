---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 79ca081726c1f26a251763e2533ade730f075e2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317269"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>语法

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>备注

**受保护的**关键字指定对*成员列表中*的类成员的访问，以下一个访问指定器（**公共**或**私有**）或类定义的结尾进行访问。 声明为**受保护的**类成员只能由以下人员使用：

- 最初声明这些成员的类的成员函数。

- 最初声明这些成员的类的友元。

- 使用公共或受保护访问（派生自最初声明这些成员的类）派生的类。

- 也对受保护成员具有专用访问权限的以私有方式派生的直接类。

在基类名称之前，**受保护**关键字指定基类的公共成员和受保护成员是其派生类的保护成员。

受保护成员不像**私有**成员那样私有，只有声明成员才能访问这些成员，但它们不像公共成员那样公开，而**公共**成员在任何功能中都可以访问。

派生类的任何友元或成员函数都可以访问也声明为**静态**的受保护成员。 派生类中的好友和成员函数只能通过指向派生类的指针、引用或对象访问未声明为**静态**的受保护成员。

有关相关信息，请参阅[控制对类成员的访问](member-access-control-cpp.md)中[的朋友](../cpp/friend-cpp.md)、[公共](../cpp/public-cpp.md)、[私有](../cpp/private-cpp.md)和成员访问表。

## <a name="clr-specific"></a>/clr 专用

在 CLR 类型中，C++访问指定器关键字（**公共**、**私有**和**受保护**）可能会影响类型和方法对程序集的可见性。 有关详细信息，请参阅[成员访问控制](member-access-control-cpp.md)。

> [!NOTE]
> 使用[/LN](../build/reference/ln-create-msil-module.md)编译的文件不受此行为的影响。 在这种情况下，所有托管类（公共或私有）都将可见。

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
[Keywords](../cpp/keywords-cpp.md)
