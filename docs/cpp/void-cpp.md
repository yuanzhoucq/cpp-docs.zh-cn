---
title: "void （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- void
- void_cpp
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: dea06f16979fab9aa4494b172d6d95193a9f3727
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="void-c"></a>void (C++)
用作函数返回类型时，`void` 关键字指定函数不返回值。 当用于函数的参数列表时，void 将指定函数不采用任何参数。 用于指针声明时，void 指定该指针为“通用”。  
  
 如果指针的类型为**void \* **，该指针可以指向任何未使用声明的变量**const**或`volatile`关键字。 void 指针不能取消引用，除非它被强制转换为另一种类型。 void 指针可以转换为任何其他类型的数据指针。  
  
 void 指针可以指向函数，但不能指向 C++ 中的类成员。  
  
 不能声明 void 类型的变量。  
  
## <a name="example"></a>示例  
  
```  
// void.cpp  
void vobject;   // C2182  
void *pv;   // okay  
int *pint; int i;  
int main() {  
   pv = &i;  
   // Cast optional in C required in C++  
   pint = (int *)pv;  
}   
```  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [基本类型](../cpp/fundamental-types-cpp.md)
