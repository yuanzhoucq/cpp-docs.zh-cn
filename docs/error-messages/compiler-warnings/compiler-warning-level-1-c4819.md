---
title: "编译器警告（等级 1）C4819 | Microsoft Docs"
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
  - "C4819"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4819"
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4819
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

该文件包含不能在当前代码页（数字）中表示的字符。以 Unicode 格式保存该文件防止数据丢失。  
  
 在具有不能表示文件中所有字符的代码页的系统上编译 ANSI 源文件时，出现 C4819。  
  
 若要解决 C4819，请以 Unicode 格式保存该文件。  在 Visual Studio 中，依次选择“文件”和“高级保存选项”。  在“高级保存选项”对话框中，选择可表示该文件中所有字符的编码（例如，UTF\-8），然后选择“确定”。