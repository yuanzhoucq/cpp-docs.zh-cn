---
title: "使用 atexit | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "atexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atexit 函数"
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 atexit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

利用 [atexit](../c-runtime-library/reference/atexit.md) 函数，您可指定在程序终止之前执行的 exit\-processing 函数。  在执行 exit\-processing 函数之前不会销毁在调用 `atexit` 之前初始化的任何全局静态对象。  
  
## 请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)