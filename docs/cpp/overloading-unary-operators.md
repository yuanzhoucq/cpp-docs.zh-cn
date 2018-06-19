---
title: 重载一元运算符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7f242fac0d81c6d46c2d810bf07459fde2fb2ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421053"
---
# <a name="overloading-unary-operators"></a>重载一元运算符
可重载的一元运算符如下：  
  
1.  `!` ([逻辑非](../cpp/logical-negation-operator-exclpt.md))  
  
2.  `&` ([地址的](../cpp/address-of-operator-amp.md))  
  
3.  `~` ([的二进制反码](../cpp/one-s-complement-operator-tilde.md))  
  
4.  `*` ([指针取消引用](../cpp/indirection-operator-star.md))  
  
5.  `+` ([一元加](../cpp/additive-operators-plus-and.md))  
  
6.  `-` ([一元求反](../cpp/additive-operators-plus-and.md))  
  
7.  `++` ([递增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
8.  `--` ([递减](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
9. 转换运算符  
  
 后缀递增和递减运算符 (`++`和**--**) 将被视为单独在[递增和递减](../cpp/increment-and-decrement-operator-overloading-cpp.md)。  
  
 转换运算符还讨论了在单独的主题;请参阅[用户定义类型转换](../cpp/user-defined-type-conversions-cpp.md)。  
  
 以下规则适用于所有其他一元运算符。 若要将一元运算符函数声明为非静态成员，则必须用以下形式声明它：  
  
 `ret-type operator` `op` `()`  
  
 其中 `ret-type` 是返回类型，`op` 是上表中列出的运算符之一。  
  
 若要将一元运算符函数声明为全局函数，则必须用以下形式声明它：  
  
 `ret-type operator` `op` (`arg` )  
  
 其中 `ret-type` 和 `op` 如上所述用于成员运算符函数，`arg` 是要参与运算的类类型的参数。  
  
> [!NOTE]
>  一元运算符的返回类型没有限制。 例如，逻辑“非”(`!`) 返回整数值是合理的，但并非强制性的。  
  
## <a name="see-also"></a>请参阅  
 [运算符重载](../cpp/operator-overloading.md)