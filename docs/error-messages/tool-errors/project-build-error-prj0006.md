---
title: "项目生成错误 PRJ0006 | Microsoft Docs"
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
  - "PRJ0006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0006"
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未能打开临时文件“file”。请确保该文件存在并且目录未被写保护。  
  
 Visual C\+\+ 在生成过程中未能创建临时文件。  原因包括：  
  
-   没有临时目录。  
  
-   临时目录是只读的。  
  
-   磁盘空间不足。  
  
-   $\(IntDir\) 文件夹是只读的或者包含只读的临时文件。  
  
 该错误还将在错误 PRJ0007（未能创建输出目录“directory”）后发生。  错误 PRJ0007 意味着未能创建 $\(IntDir\) 目录，暗指临时文件的创建也将失败。  
  
 每当指定以下各项时都会创建临时文件：  
  
-   响应文件。  
  
-   自定义生成步骤。  
  
-   生成事件。