---
title: "加 (+) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: a3e1560730f95fb3ca222f460a9da0490a609190
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="addition-"></a>加 (+)
加法运算符 (+) 导致添加其两个操作数。 两个操作数可同时为整型或浮点型，或者一个操作数为指针，另一个操作数为整数。  
  
 在将整数添加到指针时，会通过将整数值 (i) 乘以指针寻址的值的大小来转换该整数值。 转换后，整数值表示 *i* 个内存位置，其中每个位置均具有指针类型所指定的长度。 在将转换的整数值添加到指针值时，结果为表示原始地址中的地址 i 位置的新指针值。 新指针值对类型与原始指针值的类型相同的值进行寻址，因此它与数组索引相同（请参阅[一维数组](../c-language/one-dimensional-arrays.md)和[多维数组](../c-language/multidimensional-arrays-c.md)）。 如果 sum 指针指向数组的外部，除非位于在高端外的第一个位置，否则结果是不确定的。 有关详细信息，请参阅[指针算法](../c-language/pointer-arithmetic.md)。  
  
## <a name="see-also"></a>另请参阅  
 [C 加法运算符](../c-language/c-additive-operators.md)
