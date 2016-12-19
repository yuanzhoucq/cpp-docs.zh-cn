---
title: "ML Error Messages | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.errors.ml"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MASM (Microsoft Macro Assembler), ML error messages"
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Error Messages
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MASM 元素生成的错误消息分为三类:  
  
-   **错误。**这些指示防止实用工具完成其正常进程的一个严重问题。  
  
-   **非致命错误。**实用工具可以完成其过程。  如果，其结果不能为所需的脚本。  
  
-   **警告。**这些消息指示可以防止它们结果所需的行为。  
  
 所有错误消息采用以下形式:  
  
```  
  
Utility: Filename (Line) : [Error_type} (Code): Message_text  
```  
  
 其中：  
  
 `Utility`  
 发送错误消息的过程。  
  
 *文件名*  
 包含该错误的环境的文件。  
  
 *Line*  
 大致行的错误状态存在的位置。  
  
 *Error\_type*  
 错误，错误或警告。  
  
 *代码*  
 单个 5 \- 6 位数或错误代码。  
  
 `Message_text`  
 错误条件的简短、大纲显示。  
  
## 请参阅  
 [Microsoft Macro Assembler Reference](../../assembler/masm/microsoft-macro-assembler-reference.md)