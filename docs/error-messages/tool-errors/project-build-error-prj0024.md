---
title: "项目生成错误 PRJ0024 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0024"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0024"
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 项目生成错误 PRJ0024
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未能将 Unicode 路径“path”翻译成用户的 ANSI 代码页。  
  
 ***path***  是原始的 Unicode 版本的路径字符串。  如果 Unicode 路径不能直接翻译成当前系统代码页的 ANSI，则会出现该错误。  
  
 如果工作项目是在使用某个代码页的系统上开发的，而该代码页不在您的计算机上，则可能会发生此错误。  
  
 该错误的解决方法是更新路径以使用 ANSI 文本，或在计算机上安装代码页并将其设置为系统的默认代码页。