---
title: "项目生成错误 PRJ0009 | Microsoft Docs"
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
  - "PRJ0009"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0009"
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0009
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未能打开生成日志进行写入。  
  
 **请确保该文件未被其他进程打开并且未被写保护。**  
  
 将“生成记录”属性设置为**“是”**并执行生成或重新生成后，Visual C\+\+ 无法以独占模式打开生成日志。  
  
 检查“生成记录”设置，方法是打开**“选项”**对话框（在“工具”菜单上单击**“选项”**命令），然后在“项目”文件夹中选择“VC\+\+ 生成”。  生成文件名为 BuildLog.htm 并被写入中间目录 $\(IntDir\)。  
  
 此错误的可能原因为：  
  
-   您正在运行两个 Visual C\+\+ 进程，并尝试在这两个进程中同时生成同一项目的相同配置。  
  
-   生成日志文件打开时所在的进程锁定了该文件。  
  
-   用户没有创建文件的权限。  
  
-   当前用户不具有对 BuildLog.htm 文件的写访问权限。