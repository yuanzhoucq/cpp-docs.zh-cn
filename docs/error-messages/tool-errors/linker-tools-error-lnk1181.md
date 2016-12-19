---
title: "链接器工具错误 LNK1181 | Microsoft Docs"
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
  - "LNK1181"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1181"
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1181
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法打开输入文件“filename”  
  
 链接器未能找到 `filename`，因为该文件不存在或未找到路径。  
  
 以下常见原因可导致错误 LNK1181：  
  
-   `filename` 在链接器行上作为附加依赖项被引用，但该文件不存在。  
  
-   缺少用于指定包含 `filename` 的目录的 **\/LIBPATH** 语句。  
  
 若要解决上面的问题，请确保链接器行上引用的任何文件在系统中存在。另外，请确保对于包含依赖于链接器的文件的每个目录都存在 **\/LIBPATH** 语句。  
  
 导致 LNK1181 的另一可能原因是具有嵌入空格的长文件名没有括在引号内。在这种情况下，链接器仅将文件名识别到第一个空格处，然后假定文件的扩展名为 .obj。此情况的解决方案是将长文件名（路径和文件名）括在引号内。  
  
 有关更多信息，请参见[用作链接器输入的 .lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)。  
  
## 请参阅  
 [\/LIBPATH（附加的 Libpath）](../../build/reference/libpath-additional-libpath.md)