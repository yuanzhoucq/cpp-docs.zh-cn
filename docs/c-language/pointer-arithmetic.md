---
title: "指针算术 | Microsoft Docs"
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
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 4af0f378f5a89beeb8ce2ccfb4340f0b8538ce36
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="pointer-arithmetic"></a>指针算术
仅当指针操作数寻址数组成员且整数值在同一数组的边界中产生偏移时，涉及指针和整数的加法运算才会提供有意义的结果。 当整数值转换为地址偏移量时，编译器将假定只有大小相同的内存位置位于原始地址和该地址加上偏移量之间。  
  
 此假设对数组成员有效。 按照定义，数组是一系列相同类型的值；数组元素位于连续内存位置。 但是，任何类型（数组元素除外）的存储不一定由相同类型的标识符填充。 即，在内存位置（即使是相同类型的位置）之间可能会出现空白。 因此，对任何值（数组元素除外）的地址进行加法或减法的结果是不确定的。  
  
 同样，当两个指针值相减时，转换将假定只有相同类型的值（没有空白）位于操作数给定的地址之间。  
  
## <a name="see-also"></a>另请参阅  
 [C 加法运算符](../c-language/c-additive-operators.md)
