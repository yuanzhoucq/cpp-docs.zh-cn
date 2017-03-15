---
title: "项目生成错误 PRJ0035 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0035"
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 项目生成错误 PRJ0035
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文件“file”包含未能翻译成用户的 ANSI 代码页的 Unicode 内容。  
  
 ***文件的 UNICODE 内容***  
  
 ***file***  是作为 Web 部署工具的命令行而创建的 XML 文件。  
  
 项目系统在 Web 部署属性页上的某些属性中发现无法正确翻译为 ANSI 的 Unicode 字符。  
  
 此错误的解决方法是更新属性的内容以使用 ANSI，或在计算机上安装代码页并将其设置为系统的默认代码页。