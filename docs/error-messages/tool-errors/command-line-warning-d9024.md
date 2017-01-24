---
title: "命令行警告 D9024 | Microsoft Docs"
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
  - "D9024"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9024"
ms.assetid: daf4896d-223d-4af0-9b6d-89109cf3d1bb
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令行警告 D9024
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法识别的源文件类型“filename”，假定为对象文件  
  
 指定文件的扩展名未被识别。  该文件被假定为是一个对象文件并被传递到链接器。  
  
 下列扩展名可被识别：  
  
-   .c（C 源文件）  
  
-   .cxx（C\+\+ 源文件）  
  
-   .cpp（C\+\+ 源文件）  
  
-   .obj（对象文件）  
  
-   .lib（库文件）  
  
-   .def（模块定义文件）  
  
-   .exp（链接器导出文件，由 LINK \/LIB 创建）