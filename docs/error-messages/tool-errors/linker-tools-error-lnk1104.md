---
title: "链接器工具错误 LNK1104 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1104"
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具错误 LNK1104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法打开文件“filename”  
  
 工具无法打开指定文件。  
  
 通过检查以下可能的原因进行修复：  
  
-   可用磁盘空间不足。  
  
-   文件不存在。  
  
-   在项目的属性页对话框中指定库时，应该用空格（而不是逗号）分隔库名称。  
  
-   文件名或路径不正确。  
  
-   指定驱动器无效。  
  
-   没有足够的文件权限。  
  
-   `filename` 的路径超过 260 个字符。  
  
-   如果给定文件命名为 `LNKn`（这是由临时文件链接器生成的文件名），TMP 环境变量中指定的目录可能不存在，或为 TMP 环境变量指定了多个目录。 （只能为 TMP 环境变量指定一个目录路径。）  
  
-   如果库名称出现错误消息，并且你最近刚从之前的 Microsoft Visual C\+\+ 开发系统中移植了 .mak 文件，库名称可能不再有效。 确保在这种情况下库仍然存在。  
  
-   另一个程序可能已打开该文件，链接器无法向其写入。  
  
-   LIB 环境变量不正确。 有关如何更新 LIB 环境变量的信息，请参阅 [“VC\+\+ 目录”属性页](../../ide/vcpp-directories-property-page.md)。 请确保此处列出了所需的所有包含库的目录。  
  
 链接器在多个用例中使用临时文件。 即使有足够的磁盘空间，一个超大链接也会消耗地址空间或将其分成碎片。  
  
 使用以下解决方案进行修复  
  
-   使用 [\/OPT（优化）](../../build/reference/opt-optimizations.md)；消除可传递的 comdat 会多次读取所有对象文件。  
  
-   升级到 Windows XP。