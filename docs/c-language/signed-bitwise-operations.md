---
title: "带符号的按位运算 | Microsoft Docs"
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
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 9ffc5335bb28e619f166a524083937d17a59bb97
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="signed-bitwise-operations"></a>带符号的按位运算
**ANSI 3.3**：对带符号整数进行的按位运算的结果  
  
 对带符号整数进行的按位运算的工作方式与对无符号整数进行的按位运算的工作方式相同。 例如，`-16 & 99` 可用二进制格式表示  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 按位“与”的结果为 96。  
  
## <a name="see-also"></a>另请参阅  
 [整数](../c-language/integers.md)
