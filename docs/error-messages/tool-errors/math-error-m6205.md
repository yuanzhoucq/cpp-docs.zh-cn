---
title: "数学错误 M6205 | Microsoft Docs"
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
  - "M6205"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6205"
ms.assetid: fd28e7c9-a463-4a9c-a863-cc9e75315550
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 数学错误 M6205
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: \_TLOSS 错误  
  
 发生全部有效位（精度）丢失。  
  
 导致该错误的原因可能是 sin、cos 或 tan 的给定操作数太大，因为该操作数必须减小为 0 到 2\*pi 之间的数。