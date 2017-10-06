---
title: "成员访问 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
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
ms.openlocfilehash: 21cdc3de990a8b23645bb09f9f093fb0f2498254
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="member-access"></a>成员访问
可以通过重载成员访问运算符控制类成员访问 (**->**)。 此运算符被视为此用法中的一元运算符，而重载运算符函数必须是类成员函数。 因此，此类函数的声明是：  
  
## <a name="syntax"></a>语法  
  
```  
  
class-type *operator->()  
```  
  
## <a name="remarks"></a>备注  
 其中*类类型*是此运算符所属的类的名称。 成员访问运算符函数必须是非静态成员函数。  
  
 此运算符（通常与指针取消引用运算符一起使用）用于实现在取消引用用法或对用法计数前验证指针的“智能指针”。  
  
 **.** 成员访问运算符无法进行重载。  
  
## <a name="see-also"></a>另请参阅  
 [运算符重载](../cpp/operator-overloading.md)
