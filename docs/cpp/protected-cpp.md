---
title: 受保护 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- protected_cpp
dev_langs:
- C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68cf69cd0c14d56c75a2c67d4369264e7a2ee440
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406167"
---
# <a name="protected-c"></a>protected (C++)
## <a name="syntax"></a>语法  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>备注  
 **受保护**关键字指定类成员的访问权限*成员列表*到下一个访问说明符 (**公共**或**专用**) 或类定义的末尾。 类成员声明为**保护**可以仅由以下：  
  
-   最初声明这些成员的类的成员函数。  
  
-   最初声明这些成员的类的友元。  
  
-   使用公共或受保护访问（派生自最初声明这些成员的类）派生的类。  
  
-   也对受保护成员具有专用访问权限的以私有方式派生的直接类。  
  
 当基类名称前面**保护**关键字指定基类的公共和受保护成员是受保护的成员及其派生类。  
  
 受保护的成员不是专用 as**私有**成员，仅对在其中声明它们，但它们不是公共 as 类的成员可访问**公共**成员，可在中访问任何函数。  
  
 受保护的成员也声明为**静态**派生任何的类友元或成员函数可访问。 受保护的成员未声明为**静态**朋友和仅通过指针、 引用或派生类的对象的派生类中的成员函数可访问。  
  
 有关相关信息，请参阅[友元](../cpp/friend-cpp.md)，[公共](../cpp/public-cpp.md)，[专用](../cpp/private-cpp.md)，和中的成员访问表[控制对类成员的访问](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>/clr 专用  
 在 CLR 类型中，c + + 访问说明符关键字 (**公共**，**专用**，并**保护**) 可能会影响的类型和方法与程序集相关的可见性。 有关详细信息，请参阅[成员访问控制](member-access-control-cpp.md)。  
  
> [!NOTE]
>  使用文件编译[/LN](../build/reference/ln-create-msil-module.md)不受此行为。 在这种情况下，所有托管类（公共或私有）都将可见。  
  
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
  
## <a name="see-also"></a>请参阅  
 [控制对类成员的访问权限](member-access-control-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)