---
title: 间接寻址和 Address-of 运算符 | Microsoft Docs
ms.custom: ''
ms.date: 02/16/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75afd44b8c0a31d9f3731a4c6f9fb86c15de4328
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389415"
---
# <a name="indirection-and-address-of-operators"></a>间接寻址和 Address-of 运算符

一元间接寻址运算符 (&#42;) 通过指针间接访问一个值。 操作数必须是指针类型。 操作的结果是操作数所寻址的值；即其操作数指向的地址处的值。 结果的类型是操作数寻址的类型。

如果操作数的类型为指向类型的指针，则间接寻址运算符的结果为类型。 如果操作数指向函数，则结果是函数指示符。 如果指向对象，则结果为指定对象的左值。

如果指针值无效，则间接寻址运算符的结果不确定。 以下是使指针值无效的一些最常见条件：

- 该指针为 null 指针。

- 在引用过程中，该指针在对象生存期结束后（例如，对象已超出范围或已解除分配）指定其地址。

- 该指针指定未针对所指向的对象类型正确对齐的地址。

- 该指针指定执行程序未使用的地址。

一元 address-of 运算符 (&) 给出其操作数的地址。 操作数必须是用于指定对象的左值，该对象不得声明为“register”，也不得为位域、一元 &#42; 运算符或数组取消引用 (&#91;&#93;) 运算符的结果或函数指示符。 操作数类型为类型时，结果的类型为指向类型的指针。

如果操作数是一元 &#42; 运算符的结果，则不对两个运算符进行运算，并且结果像是同时省略了这两个运算符。 结果不为左值，运算符约束仍适用。 如果操作数是 &#91;&#93; 运算符的结果，则不会对 & 运算符进行运算，也不会对 &#91;&#93; 运算符暗含的一元 &#42; 进行运算。 其结果与删除 & 运算符并将 &#91;&#93; 运算符更改为 + 运算符的效果相同。 否则，结果为指向对象或操作数指定的函数的指针。


## <a name="examples"></a>示例

下面的示例使用这些常用声明：

```C
int *pa, x;
int a[20];
double d;
```

此语句使用 address-of 运算符 (&) 来获取数组 `a` 的第六个元素的地址。 结果存储在指针变量 `pa` 中：

```C  
pa = &a[5];
```

间接寻址运算符 (&#42;) 在此示例中用于访问存储在 `pa` 中的地址的 `int` 值。 将此值分配给整数变量 `x`：

```C
x = *pa;
```

此示例表明对 `x` 的地址应用间接运算符的结果与 `x` 相同：

```C
assert( x == *&x );
```

此示例演示用于声明指向函数的指针的等效方法：

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```  

一旦声明函数 `roundup`，将声明并初始化指向 `roundup` 的两个指针。 第一个指针为 `proundup`，它仅通过函数名称进行初始化；第二个指针为 `pround`，它在初始化中使用 address-of 运算符。 初始化是等效的。

## <a name="see-also"></a>请参阅

[间接寻址运算符：&#42;](../cpp/indirection-operator-star.md)  
[Address-of 运算符：&](../cpp/address-of-operator-amp.md)  
