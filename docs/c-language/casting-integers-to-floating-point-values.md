---
title: "将整数强制转换为浮点值 | Microsoft Docs"
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
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d926b50cdd8caef1a1119aaf319bfae88970651
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="casting-integers-to-floating-point-values"></a>将整数转换为浮点值
**ANSI 3.2.1.3** 当一个整数转换为无法确切表示原始值的浮点数时的截断方向  
  
 当一个整数转换为无法确切表示值的浮点值时，值将被舍入（向上或向下）到最接近的适当值。  
  
 例如，将 unsigned long（具有 32 位精度）转换为 float（尾数具有 23 位精度）会将该数字舍入到 256 的最接近倍数。 介于 4,294,966,913 和 4,294,967,167 之间的所有 long 值都将舍入到 float 值 4,294,967,040。  
  
## <a name="see-also"></a>请参阅  
 [浮点数学](../c-language/floating-point-math.md)