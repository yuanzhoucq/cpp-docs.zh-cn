---
title: "BSCMAKE 错误 BK1513 | Microsoft Docs"
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
  - "BK1513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1513"
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 错误 BK1513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非增量更新要求所有的 .SBR 文件  
  
 BSCMAKE 无法生成新的浏览信息 \(.bsc\) 文件，因为一个或多个 .sbr 文件被截断。  若要查找已截断的 .sbr 文件的名称，请阅读伴随此错误出现的 [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) 警告。  
  
 BSCMAKE 可使用截断的 .sbr 文件更新 .bsc 文件，但不能生成新文件。  BSCMAKE 可能生成新的 .bsc 文件，原因如下：  
  
-   缺少 .bsc 文件。  
  
-   为 .bsc 文件指定的文件名出错。  
  
-   .bsc 文件损坏。  
  
 若要解决此问题，请删除截断的 .sbr 文件并重新生成，或者清除解决方案并重新生成。  （在 IDE 中，选择“生成”，“清理解决方案”，然后选择“生成”，“重新生成解决方案”。）