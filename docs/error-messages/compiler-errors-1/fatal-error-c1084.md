---
title: "错误 C1084 | Microsoft Docs"
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
  - "C1084"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1084"
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1084
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法读取 filetype 文件：“file”: 消息  
  
 此错误通常是由编译器无法执行内部系统 API 调用造成的。  遇到此错误时显示的消息通常是由 [\_wcserror\_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) 或 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351.aspx) 生成的。  
  
 执行以下步骤可帮助解决 C1084 错误：  
  
-   请确保指定的文件存在。  
  
-   请确保设置了访问指定文件所需的相应权限。  
  
-   请确保命令行语法符合[编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)下概括的规则。  
  
-   请确保环境变量 **TMP** 和 **TEMP** 设置正确，并设置访问这些环境变量所引用的目录所需的相应权限。  还要确保 **TMP** 和 **TEMP** 环境变量所引用的驱动器有足够的可用空间。  
  
-   如果消息指出“文件号错误”，说明指定的文件在后台进行编译的同时，可能已在前台关闭。  
  
 执行上面的诊断后，请执行干净的生成。