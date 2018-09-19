---
title: 下标运算符的解释 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1457744747ee3638d7f0b9485ac12af60e5cdd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058336"
---
# <a name="interpretation-of-subscript-operator"></a>下标运算符的解释

像其他运算符，下标运算符 (**\[]**) 可以由用户重新定义。 如果没有重载下标运算符，下标运算符的默认行为是使用以下方法组合数组名称和下标：

\*((*数组名称*) + (*下标*))

像涉及指针类型的所有加法中一样，缩放将自动执行以调整类型的大小。 因此，所得到的值不是*下标*字节的来源*数组名称*; 而是，它是*下标*个元素的数组。 (有关此转换的详细信息，请参阅[相加运算符](../cpp/additive-operators-plus-and.md)。)

同样，对于多维数组，将使用以下方法获取地址：

((*数组名称*) + (*下标*1 \* *max*2 \* *max*3 \* ...\* *最大*n) + (*下标*2 \* *最大*3 \* ...\* *最大*n) +...+*下标*n))

## <a name="see-also"></a>请参阅

[数组](../cpp/arrays-cpp.md)<br/>
