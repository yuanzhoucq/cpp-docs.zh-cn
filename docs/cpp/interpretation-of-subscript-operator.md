---
title: 下标运算符的解释
ms.date: 08/27/2018
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
ms.openlocfilehash: 1c3d5bca66cb294503805fd5b7691331ac380ae5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375309"
---
# <a name="interpretation-of-subscript-operator"></a>下标运算符的解释

像其他运算符，下标运算符 (**\[]**) 可以由用户重新定义。 如果没有重载下标运算符，下标运算符的默认行为是使用以下方法组合数组名称和下标：

\*((*array-name*) + (*subscript*))

像涉及指针类型的所有加法中一样，缩放将自动执行以调整类型的大小。 因此，所得到的值不是*下标*字节的来源*数组名称*; 而是，它是*下标*个元素的数组。 (有关此转换的详细信息，请参阅[相加运算符](../cpp/additive-operators-plus-and.md)。)

同样，对于多维数组，将使用以下方法获取地址：

((*数组名称*) + (*下标*1 \* *max*2 \* *max*3 \* ...\* *最大*n) + (*下标*2 \* *最大*3 \* ...\* *最大*n) +...+*下标*n))

## <a name="see-also"></a>请参阅

[数组](../cpp/arrays-cpp.md)<br/>
