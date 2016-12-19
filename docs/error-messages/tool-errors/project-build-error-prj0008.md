---
title: "项目生成错误 PRJ0008 | Microsoft Docs"
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
  - "PRJ0008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0008"
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未能删除文件“file”。  
  
 **请确保该文件未被其他进程打开并且未被写保护。**  
  
 重新生成或清理期间，Visual C\+\+ 删除生成的所有已知的中间文件和输出文件，以及任何满足[常规配置设置属性页](../../ide/general-property-page-project.md)中“清除时要删除的扩展名”属性中的通配符规范的文件。  
  
 如果 Visual C\+\+ 无法删除文件，您将看到该错误。  若要解决此错误，需使执行生成的用户对文件及其目录有写权限。