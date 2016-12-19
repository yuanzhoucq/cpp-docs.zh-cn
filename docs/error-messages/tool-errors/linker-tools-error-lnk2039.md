---
title: "链接器工具错误 LNK2039 | Microsoft Docs"
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
  - "LNK2039"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2039"
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK2039
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

导入在 another.obj 定义的 ref “\<类型\>”;应导入或定义它，但不能同时为两者，  
  
 ref 类 '\<中的`type`\>' 指定的 .obj 文件。其他 .obj 文件导入，但是还定义。  此情况可能导致运行时失败或其他意外行为。  
  
### 更正此错误  
  
1.  检查是否在其他的 .obj 文件和检查必须定义 '`type`' 是否必须从 .winmd 文件导入该文件。  
  
2.  定义或移除导入。  
  
## 请参阅  
 [链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)   
 [链接器工具错误 LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)