---
title: "地址存储 | Microsoft Docs"
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
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 3d0e996ac191ba3091925a85937e7636a2425215
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="storage-of-addresses"></a>地址存储
地址所需的存储量和该地址的含义取决于编译器的实现。 指向不同类型的指针不能保证具有相同的长度。 因此，sizeof(char \*) 不必与 sizeof(int \*) 相等。  
  
 **Microsoft 专用**  
  
 对于 Microsoft C 编译器，sizeof(char \*) 与 sizeof(int \*) 相等。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [指针声明](../c-language/pointer-declarations.md)
