---
title: 编译器错误 C2228 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2228
dev_langs:
- C++
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 969f622877c60bdc340dedf8a2416ac56b2ad0e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171020"
---
# <a name="compiler-error-c2228"></a>编译器错误 C2228
“.identifier”的左边必须有类/结构/联合  
  
 句点 （.） 左侧的操作数不是类、 结构或联合。  
  
 下面的示例生成 C2228：  
  
```  
// C2228.cpp  
int i;  
struct S {  
public:  
    int member;  
} s, *ps = &s;  
  
int main() {  
   i.member = 0;   // C2228 i is not a class type  
   ps.member = 0;  // C2228 ps is a pointer to a structure  
  
   s.member = 0;   // s is a structure type  
   ps->member = 0; // ps points to a structure S  
}  
```  
  
 如果在使用托管扩展时用了不正确的语法，也会看到此错误。 而在其他 Visual Studio 语言中，可以使用点运算符访问托管类的成员，指向 C++ 中对象的指针意味着你需要使用 -> 运算符来访问该成员:  
  
 错误： `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`  
  
 正确： `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`