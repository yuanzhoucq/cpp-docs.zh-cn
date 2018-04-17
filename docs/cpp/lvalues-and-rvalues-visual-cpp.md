---
title: 值的分类： 左值和右值 （Visual C++） |Microsoft 文档
ms.custom: ''
ms.date: 04/06/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6512be9e64cdd5fb56d94fe1842be4f38d93d52c
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="lvalues-and-rvalues-visual-c"></a>左值和右值 （Visual C++）

每个 C++ 表达式有一个类型，并且属于*值类别*。 值类别是在创建、 复制和表达式求值期间移动临时对象时，编译器必须遵循的规则的基础。

 C++ 17 标准定义表达式值的分类，如下所示：

- A *glvalue*是求值确定的标识的对象、 位域或函数的表达式。
- A *prvalue*是一个表达式求值初始化对象或一个位字段，或在它所出现的上下文中的指定计算运算符的操作数的值。
- *Xvalue*是表示的对象或位域 （通常是因为它是在其生存期结束时的附近），可以重用其资源 glvalue。 [示例： 某些类型的表达式涉及右值引用 (8.3.2) 产生 xvalues，如对其返回类型是右值引用的函数的调用或强制转换为右值引用类型。 ]
- *左值*是不是 xvalue glvalue。
- *右值*prvalue 或 xvalue。

下图阐释了两个分类之间的关系：

 ![C++ 表达式值的分类](media/value_categories.png "C++ 表达式值的分类")

 左值具有可以访问你的程序的地址。 左值表达式的示例包括变量名称，包括`const`变量，数组元素，函数返回左值引用、 位域、 联合和类成员的调用。

 Prvalue 表达式中有任何由你的程序可访问的地址。 Prvalue 表达式的示例包括文本、 非引用类型返回的函数调用和只能由编译器创建表达式评估过程中，但可访问的临时对象。

 Xvalue 表达式具有的地址，无法再进行访问由你的程序，但可以用于初始化右值引用，它提供的表达式的访问。 示例包括返回右值引用，数组下标、 成员和指针到成员表达式，该数组或对象是右值引用的函数调用。

## <a name="example"></a>示例

 以下示例演示左值和右值的多种正确的和错误的用法：

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
 int i, j, *p;

 // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
 i = 7;

 // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
 7 = i; // C2106
 j * 4 = 7; // C2106

 // Correct usage: the dereferenced pointer is an lvalue.
 *p = i;

 const int ci = 7;
 // Incorrect usage: the variable is a non-modifiable lvalue (C3892).
 ci = 9; // C3892

 // Correct usage: the conditional operator returns an lvalue.
 ((i < 3) ? i : j) = 7;
}
```

> [!NOTE]
> 此主题中的示例阐释了未重载运算符时的正确和错误用法。 通过重载运算符，可以使表达式（如 `j * 4`）成为左值。

条款*左值*和*右值*通常用于在引用对象引用时。 有关引用的详细信息，请参阅[左值引用声明符： &](../cpp/lvalue-reference-declarator-amp.md)和[右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另请参阅

 [基本概念](../cpp/basic-concepts-cpp.md)[左值引用声明符： &](../cpp/lvalue-reference-declarator-amp.md) [右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)