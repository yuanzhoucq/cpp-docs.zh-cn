---
title: "提取库成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EXTRACT 库管理器选项"
  - "EXTRACT 库管理器选项"
  - "-EXTRACT 库管理器选项"
  - "提取库成员"
  - "LIB [C++], 提取库成员"
  - "库, 提取成员"
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 提取库成员
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可使用 LIB 创建包含现有库成员副本的对象 \(.obj\) 文件。  若要提取成员副本，请使用下列语法：  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 此命令创建一个名为 *objectfile* 的 .obj 文件，它包含 *library* 的 `member` 副本。  `member` 名区分大小写。  在单个命令中只能提取一个成员。  \/OUT 选项为必选项；不存在默认输出名。  如果名为 *objectfile* 的文件已存在于指定目录（如果未用 *objectfile* 指定任何目录，则为当前目录）中，则提取的 *objectfile* 替换现有文件。  
  
## 请参阅  
 [LIB 引用](../../build/reference/lib-reference.md)