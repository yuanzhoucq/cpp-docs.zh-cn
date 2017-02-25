---
title: "_ITERATOR_DEBUG_LEVEL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ITERATOR_DEBUG_LEVEL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ITERATOR_DEBUG_LEVEL"
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _ITERATOR_DEBUG_LEVEL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

IDL \( `_ITERATOR_DEBUG_LEVEL` \) 并将 SCL 宏取代 [\_SECURE\_SCL](../standard-library/secure-scl.md) \(\) 和 [\_HAS\_ITERATOR\_DEBUGGING](../standard-library/has-iterator-debugging.md) \(隐藏\) 宏的功能。  
  
## 宏值  
 下表汇总了 `_SECURE_SCL` 和 `_HAS_ITERATOR_DEBUGGING` 宏的值，最后这些值如何由 `_ITERATOR_DEBUG_LEVEL` 宏取代。  
  
 以下各节介绍 SCL 和隐藏宏的可能值。  
  
 SCL\=0  
 禁用 CHECK 迭代器。  
  
 SCL\=1  
 使检查迭代器。  
  
 HID\=0  
 禁用迭代器的调试版本。  
  
 HID\=1  
 支持迭代器的调试版本。  HID 在发布版本无法启用。  
  
 下表描述的 IDL 宏取代值如何 SCL 和隐藏宏的值。  
  
|编译模式|新的宏|旧宏|说明|  
|----------|---------|--------|--------|  
|**调试**||||  
||IDL\=0|SCL\=0，HID\=0|禁用 CHECK 迭代器并禁用调试。迭代器|  
||IDL\=1|SCL\=1，HID\=0|使检查迭代器并禁用调试。迭代器|  
||IDL\=2 \(默认\)|\(不 SCL\= 应用程序\)，HID\=1|默认情况下，支持迭代器；调试检查的迭代器是不相关的。|  
|**Release**||||  
||IDL\=0 \(默认\)|SCL\=0|默认情况下，禁用 CHECK 迭代器。|  
||IDL\=1|SCL\=1|使检查迭代器；迭代器在调试不相关。|  
  
## 备注  
 在发布模式，因此，如果指定 IDL\=2.，错误发出。  
  
 由于 `_SECURE_SCL` 宏和 `_HAS_ITERATOR_DEBUGGING` 支持类似的功能，使用的宏和宏值在特定情况的用户通常是不确定的。  若要解决此问题，我们建议您仅使用 `_ITERATOR_DEBUG_LEVEL` 宏。  
  
## 请参阅  
 [安全库：C\+\+ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)