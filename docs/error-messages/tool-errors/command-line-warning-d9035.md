---
title: "命令行警告 D9035 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D9035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9035"
ms.assetid: 6254f933-e37a-45ba-b860-1a870d1bc8e8
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 命令行警告 D9035
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“option”选项已否决，并将在将来的版本中移除  
  
 您指定了将在 Visual C\+\+ 编译器的未来版本中移除的编译器选项。  如果存在*option*的建议替换项，则此警告后还会有 [D9036](../../error-messages/tool-errors/command-line-warning-d9036.md) 警告。  
  
 指定选项仍然起作用，但您应立即更新生成配置。  因此，当您升级编译器时，您的项目很可能将继续生成。  
  
## 请参阅  
 [命令行警告 D9036](../../error-messages/tool-errors/command-line-warning-d9036.md)