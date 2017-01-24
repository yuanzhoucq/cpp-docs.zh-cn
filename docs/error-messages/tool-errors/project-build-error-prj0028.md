---
title: "项目生成错误 PRJ0028 | Microsoft Docs"
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
  - "PRJ0028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0028"
ms.assetid: 0a6e0da7-cb3d-40b6-81a6-6196a9c2526b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

临时文件“file”包含未能翻译成用户的 ANSI 代码页的 Unicode 内容。  
  
 用 [\/MIDL（指定 MIDL 命令行选项）](../../build/reference/midl-specify-midl-command-line-options.md)链接器选项指定了一个值，但该值未能被系统代码页解析。  
  
 指定 MIDL 命令时使用的代码页（输入代码页）必须与系统代码页相同。