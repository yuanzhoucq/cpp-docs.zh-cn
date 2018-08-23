---
title: 分配 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6343d7be23e633fe383343bd7f154d5cc9bb234
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407606"
---
# <a name="assignment"></a>赋值
赋值运算符 (**=**) 严格地说，是二元运算符。 其声明与任何其他二元运算符的相同，但有以下例外：  
  
-   它必须是非静态成员函数。 否**运算符 =** 可以声明为非成员函数。  
  
-   它不由派生类继承。  
  
-   默认值**运算符 =** 类类型的编译器可以生成函数，如果不存在。  
  
 以下示例阐释如何声明赋值运算符：  
  
```cpp 
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
  
```cpp 
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>请参阅  
 [运算符重载](../cpp/operator-overloading.md)