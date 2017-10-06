---
title: Naked (C) | Microsoft Docs
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
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 24266f2241ddb60d4a5403447a87caaa08ddaf08
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="naked-c"></a>Naked (C)
**Microsoft 专用**  
  
 裸存储类特性是特定于 Microsoft 的 C 语言扩展。 编译器生成代码，而没有使用裸存储类特性声明的函数的 prolog 和 epilog 代码。 当您需要使用内联汇编代码编写自己的 prolog/epilog 代码序列时，裸函数很有用。 裸函数对于编写虚拟设备驱动程序很有用。  
  
 有关使用 naked 特性的特定信息，请参阅 [Naked 函数](../c-language/naked-functions.md)。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [C 扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)
