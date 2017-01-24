---
title: "资源编译器警告 RW4004 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW4004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW4004"
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器警告 RW4004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不等效于虚键控代码的 ASCII 字符  
  
 字符串用于 VIRTKEY 类型快捷键中的虚键控代码。  
  
 该警告允许您继续，但请注意：生成的快捷键可能与您指示的字符串不匹配。（VIRTKEY 使用不同于 ASCII 快捷键的其他键控代码。）  
  
 尽管字符串在语法上有效，您只能通过使用 WINDOWS.h 中的 **VK\_\* \#define** 值确保获得所需的快捷键。