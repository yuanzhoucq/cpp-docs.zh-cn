---
title: "NMAKE 错误 U1087 | Microsoft Docs"
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
  - "U1087"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1087"
ms.assetid: 5236ab54-e117-484d-99c3-852b061fd3d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 错误 U1087
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

同一目标不能有 : 和 :: 从属项  
  
 既不能在单冒号 \(**:**\) 依赖项也不能在双冒号 \(`::`\) 依赖项中指定目标。  
  
 若要在多个描述块中指定目标，请在每个依赖项行中使用 `::`。