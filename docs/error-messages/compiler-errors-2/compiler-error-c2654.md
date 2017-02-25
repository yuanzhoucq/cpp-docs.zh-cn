---
title: "编译器错误 C2654 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2654"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2654"
ms.assetid: ca7de1bd-576b-40bf-96fc-a91984827d20
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2654
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 尝试访问成员函数的外部成员  
  
 在声明中访问了某成员。  成员数据仅可在成员函数中进行访问。  
  
 当尝试在声明中初始化变量时，可能会导致此错误。  为此，请使用构造函数。