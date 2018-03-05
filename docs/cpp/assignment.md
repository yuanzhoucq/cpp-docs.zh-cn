---
title: "分配 |Microsoft 文档"
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
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4c11664b5a7089187099898fa375cd612e92a83b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="assignment"></a>赋值
赋值运算符 (**=**) 严格地说，是二元运算符。 其声明与任何其他二元运算符的相同，但有以下例外：  
  
-   它必须是非静态成员函数。 没有 `operator=` 可声明为非成员函数。  
  
-   它不由派生类继承。  
  
-   默认 `operator=` 函数可由类类型的编译器生成（如果该函数不存在）。 (有关默认详细信息`operator=`函数，请参阅[成员赋值和初始化](http://msdn.microsoft.com/en-us/94048213-8b49-4416-8069-b1b7a6f271f9)。)  
  
 以下示例阐释如何声明赋值运算符：  
  
```  
// assignment.cpp  
class Point  
{  
public:  
   Point &operator=( Point & );  // Right side is the argument.  
   int _x, _y;  
};  
  
// Define assignment operator.  
Point &Point::operator=( Point &ptRHS )  
{  
   _x = ptRHS._x;  
   _y = ptRHS._y;  
  
   return *this;  // Assignment operator returns left side.  
}  
  
int main()  
{  
}  
```  
  
 请注意，所提供的参数是表达式的右侧。 此运算符返回对象以保留赋值运算符的行为，赋值运算符在赋值完成后返回左侧的值。 这使您可以编写类似于下面的语句：  
  
```  
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>请参阅  
 [运算符重载](../cpp/operator-overloading.md)