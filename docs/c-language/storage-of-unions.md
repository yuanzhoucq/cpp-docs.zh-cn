---
title: "联合的存储 |Microsoft Docs"
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
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: cb349b2c1649b6e4e46fcc92829de87043d0c50a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="storage-of-unions"></a>联合的存储
与联合变量关联的存储是联合的最大成员所需的存储。 在存储较小的成员时，联合变量可以包含未使用的内存空间。 所有成员都存储在同一内存空间中并以相同的地址开始。 每次将值赋给不同的成员时，都会重写存储的值。 例如:   
  
```  
union         /* Defines a union named x */  
{  
    char *a, b;  
    float f[20];  
} x;  
```  
  
 `x` 联合的成员（按照其声明的顺序）是指向 `char` 值、`char` 值和 float 值的数组的指针。 由于 `x` 是联合的最长成员，因此为 `f` 分配的存储是 20 个元素数组 `f` 所需的存储。 由于没有与联合关联的标记，因此其类型是未命名的或“匿名的”。  
  
## <a name="see-also"></a>另请参阅  
 [联合声明](../c-language/union-declarations.md)
