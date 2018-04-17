---
title: 受保护 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- protected_cpp
dev_langs:
- C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02366a53f02142f66aa5dca493c5460c9f2d1d92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="protected-c"></a>protected (C++)
## <a name="syntax"></a>语法  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>备注  
 `protected`关键字指定类成员的访问权限*成员列表*到下一个访问说明符 (**公共**或`private`) 或类定义的末尾。 只能通过以下项使用声明为 `protected` 的类成员：  
  
-   最初声明这些成员的类的成员函数。  
  
-   最初声明这些成员的类的友元。  
  
-   使用公共或受保护访问（派生自最初声明这些成员的类）派生的类。  
  
-   也对受保护成员具有专用访问权限的以私有方式派生的直接类。  
  
 当以基类的名称开头时，`protected` 关键字指定基类的公共成员和保护成员是其派生类的保护成员。  
  
 受保护的成员不为私有 as`private`成员，只有在其中声明它们，但它们不是为作为公共类的成员能够访问**公共**中任何函数均可访问的成员。  
  
 受保护成员也声明为**静态**向派生任何的类友元或成员函数可访问。 受保护成员未声明为**静态**朋友和仅通过指针引用或所派生的类的对象的派生类中的成员函数可访问。  
  
 有关相关信息，请参阅[友元](../cpp/friend-cpp.md)，[公共](../cpp/public-cpp.md)，[私有](../cpp/private-cpp.md)，和中的成员访问表[控制对类成员的访问](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>/clr 专用  
 在 CLR 类型中，C++ 访问说明符关键字 (**公共**，`private`，和`protected`) 可能会影响类型和方法与程序集相关的可见性。 有关详细信息，请参阅[成员访问控制](member-access-control-cpp.md)。  
  
> [!NOTE]
>  与已编译的文件[/LN](../build/reference/ln-create-msil-module.md)不受此行为。 在这种情况下，所有托管类（公共或私有）都将可见。  
  
## <a name="end-clr-specific"></a>END /clr 专用  
  
## <a name="example"></a>示例  
  
```  
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
  
## <a name="see-also"></a>请参阅  
 [控制对类成员访问](member-access-control-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)