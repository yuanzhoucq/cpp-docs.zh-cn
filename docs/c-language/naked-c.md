---
title: Naked (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a60cdec00f3109bfcc332feeaca24ba5d6880f9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="naked-c"></a>Naked (C)
**Microsoft 专用**  
  
 裸存储类特性是特定于 Microsoft 的 C 语言扩展。 编译器生成代码，而没有使用裸存储类特性声明的函数的 prolog 和 epilog 代码。 当您需要使用内联汇编代码编写自己的 prolog/epilog 代码序列时，裸函数很有用。 裸函数对于编写虚拟设备驱动程序很有用。  
  
 有关使用 naked 特性的特定信息，请参阅 [Naked 函数](../c-language/naked-functions.md)。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [C 扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)