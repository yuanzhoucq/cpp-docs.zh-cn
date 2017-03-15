---
title: "链接器工具警告 LNK4070 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4070"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4070"
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具警告 LNK4070
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

.EXP 中的 \/OUT:filename 指令与输出文件名“filename”不同；忽略指令  
  
 创建 .exp 文件时在 [NAME](../../build/reference/name-c-cpp.md) 或 [LIBRARY](../../build/reference/library.md) 语句中指定的 `filename` 不同于默认情况下采用的或用 [\/OUT](../../build/reference/out-output-file-name.md) 选项指定的输出 `filename`。  
  
 如果在开发环境中更改输出文件的名称并且项目的 .def 文件未更新，将显示此警告。  手动更新 .def 文件以解决此警告。  
  
 使用结果 DLL 的客户程序可能会遇到问题。