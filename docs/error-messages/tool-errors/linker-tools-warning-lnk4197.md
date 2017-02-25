---
title: "链接器工具警告 LNK4197 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4197"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4197"
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 链接器工具警告 LNK4197
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

多次指定导出“exportname”；使用第一个规范  
  
 用多个不同的方式指定了导出。  链接器使用第一个规范，而忽略其余的规范。  
  
 如果您正在重新生成 C 运行库，则可以忽略此消息。  
  
 如果以完全相同的方式多次指定一个导出，链接器将不发出警告。  
  
 例如，.def 文件的下列内容将导致此警告：  
  
```  
EXPORTS  
   functioname      NONAME  
   functioname      @10  
```  
  
### 通过检查以下可能的原因进行修复  
  
1.  在命令行（通过 export:）上和 .def 文件中指定了同一个导出  
  
2.  同一个导出在 .def 文件中列出两次，但具有不同的特性。