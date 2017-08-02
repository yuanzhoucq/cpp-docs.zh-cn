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
ms.openlocfilehash: 8a9a2b431a6f064d4593a547092a7e6dcf60dadd
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="storage-of-addresses"></a>地址存储
地址所需的存储量和该地址的含义取决于编译器的实现。 指向不同类型的指针不能保证具有相同的长度。 因此，sizeof(char \*) 不必与 sizeof(int \*) 相等。  
  
 **Microsoft 专用**  
  
 对于 Microsoft C 编译器，sizeof(char \*) 与 sizeof(int \*) 相等。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [指针声明](../c-language/pointer-declarations.md)
