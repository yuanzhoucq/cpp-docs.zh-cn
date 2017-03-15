---
title: "编译器警告 C4335 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4335"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4335"
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器警告 C4335
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检测到 Mac 文件格式: 请将源文件转换为 DOS 格式或 UNIX 格式  
  
 源文件第一行的行终止字符是 Macintosh 样式 \(‘\\r’\)，而不是 UNIX \(‘\\n’\) 或 DOS \(‘\\r\\n’\) 样式。  
  
 此警告始终作为错误发出。有关如何禁用此警告的信息，请参见[警告](../../preprocessor/warning.md)编译提示。并且，此警告只在每次编译时发出一次。  因此，如果存在多个指定 Macintosh 格式文件的 `#include` 指令，C4335 警告将只发出一次。  
  
 生成 Macintosh 格式文件的一种方法是使用 Visual Studio 中的**“高级保存选项”**（在**“文件”**菜单上）。  
  
## 示例  
 下面的示例生成 C4335。  
  
```  
// C4335 expected  
#include "c4335.h"   // assume both include files are in Macintosh format  
#include "c4335_2.h"  
```