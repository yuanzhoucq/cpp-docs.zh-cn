---
title: "编译器错误 C3292 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3292"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3292"
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3292
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

cli 命名空间不能重新打开  
  
 cli 命名空间不能在代码中声明。  有关更多信息，请参见[Platform、default 和 cli 命名空间](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
## 示例  
 以下示例生成 C3292。  
  
```  
// C3292.cpp // compile with: /clr /c namespace cli {};   // C3292  
```