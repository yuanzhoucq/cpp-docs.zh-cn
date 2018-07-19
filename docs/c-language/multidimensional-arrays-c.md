---
title: 多维数组 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25ca58d9818782b51e6c07bb6bb758948adab3ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387947"
---
# <a name="multidimensional-arrays-c"></a>多维数组 (C)
下标表达式还可以有多个下标，如下所示：  
  
```  
  
expression1  
[  
expression2  
] [  
expression3  
]...  
```  
  
 下标表达式从左至右关联。 首先计算最左侧的下标表达式 expression1[expression2]。 通过添加 expression1 和 expression2 得到的地址构成一个指针表达式；然后 expression3 将添加到此指针表达式，从而构成一个新的指针表达式，依此类推，直到添加最后一个下标表达式。 在计算最后一个下标表达式之后应用间接寻址运算符 (\*)，除非最终指针值寻址数组类型（请参阅以下示例）。  
  
 具有多个下标的表达式引用“多维数组”的元素。 多维数组是其元素为数组的数组。 例如，三维数组的第一个元素是一个具有两个维度的数组。  
  
## <a name="examples"></a>示例  
 在下面的示例中，将使用 3 个元素声明名为 `prop` 的数组，其中每个元素都是 `int` 值的 4 x 6 数组。  
  
```  
int prop[3][4][6];  
int i, *ip, (*ipp)[6];  
```  
  
 对 `prop` 数组的引用如下所示：  
  
```  
i = prop[0][0][1];  
```  
  
 上面的示例演示如何引用 `int` 的第二个单独的 `prop` 元素。 数组将按行存储，因此最后一个下标变化最快；表达式 `prop[0][0][2]` 引用数组的下一个（第三个）元素，依此类推。  
  
```  
i = prop[2][1][3];  
```  
  
 此语句是对 `prop` 的单个元素的更复杂的引用。 此表达式的计算方式如下：  
  
1.  第一个下标 `2` 乘以 4 x 6 `int` 数组的大小，然后与指针值 `prop` 相加。 结果将指向 `prop` 的第三个 4 x 6 数组。  
  
2.  第二个下标 (`1`) 乘以 6 元素 `int` 数组的大小，然后与 `prop[2]` 表示的地址相加。  
  
3.  6 元素数组的每个元素都是一个 `int` 值，因此最后一个下标 `3` 在与 `int` 相加之前将乘以 `prop[2][1]` 的大小。 生成的指针将寻址到 6 元素数组的第四个元素。  
  
4.  将对指针值应用间接寻址运算符。 结果是该地址处的 `int` 元素。  
  
 下面两个示例演示未应用间接寻址运算符的情况。  
  
```  
ip = prop[2][1];  
  
ipp = prop[2];  
```  
  
 在上面的第一个语句中，表达式 `prop[2][1]` 是对三维数组 `prop` 的有效引用；它引用一个 6 元素数组（上面已声明）。 由于指针值将寻址到一个数组，因此不会应用间接寻址运算符。  
  
 同样，第二个语句 `prop[2]` 中的表达式 `ipp = prop[2];` 的结果是一个寻址到一个二维数组的指针值。  
  
## <a name="see-also"></a>请参阅  
 [下标运算符：](../cpp/subscript-operator.md)