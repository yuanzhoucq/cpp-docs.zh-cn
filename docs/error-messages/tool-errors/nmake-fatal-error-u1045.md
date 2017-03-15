---
title: "NMAKE 错误 U1045 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1045"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1045"
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# NMAKE 错误 U1045
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成失败：消息  
  
 由于给定原因，NMAKE 调用的程序或命令失败。  当 NMAKE 调用另一个程序（例如，编译器或链接器）时，调用可能会失败，或者可能由调用的程序返回一个错误。  此消息用于报告错误。  
  
 若要解决此问题，请首先确定错误原因。  你可以使用 NMAKE [\/N](../../build/nmake-options.md) 选项报告的命令来验证环境设置和重复命令行上 NMAKE 执行的操作。