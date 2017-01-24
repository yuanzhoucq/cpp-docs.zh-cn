---
title: "命令宏和选项宏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE 中的命令宏"
  - "宏, 命令宏"
  - "宏, options 宏"
  - "options 宏"
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令宏和选项宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为 Microsoft 产品预定义命令宏。  选项宏表示这些产品的选项，并且在默认情况下不定义。  两者都用于预定义的推理规则并可用于描述块或用户定义的推理规则。  命令宏可以重新定义以表示部分或整个命令行，包括选项。  如果不定义，选项宏生成空字符串。  
  
|Microsoft 产品|命令宏|定义为|选项宏|  
|------------------|---------|---------|---------|  
|宏汇编|**AS**|ml|**AFLAGS**|  
|Basic 编译器|**BC**|bc|**BFLAGS**|  
|C 编译器|**CC**|cl|**CFLAGS**|  
|C\+\+ 编译器|**CPP**|cl|**CPPFLAGS**|  
|C\+\+ 编译器|**CXX**|cl|**CXXFLAGS**|  
|资源编译器|**RC**|rc|**RFLAGS**|  
  
## 请参阅  
 [特殊 NMAKE 宏](../build/special-nmake-macros.md)