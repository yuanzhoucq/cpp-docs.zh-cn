---
title: "编译器错误 C2857 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2857"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2857"
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2857
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在源文件中没有找到用 \/Ycfilename 命令行选项指定的“\#include”语句  
  
 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 选项指定不包括在要编译的源文件中的包含文件名。  
  
 在未编译的条件编译块中使用 `#include` 语句会导致此错误。