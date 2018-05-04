---
title: void （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- void_cpp
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de70ec6758109bc765d0cec3552762288d51ded2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="void-c"></a>void (C++)
用作函数返回类型时，`void` 关键字指定函数不返回值。 当用于函数的参数列表时，void 将指定函数不采用任何参数。 用于指针声明时，void 指定该指针为“通用”。  
  
 如果指针的类型为**void \*** ，该指针可以指向任何未使用声明的变量**const**或`volatile`关键字。 void 指针不能取消引用，除非它被强制转换为另一种类型。 void 指针可以转换为任何其他类型的数据指针。  
  
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
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [基本类型](../cpp/fundamental-types-cpp.md)