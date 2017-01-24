---
title: "资源编译器错误 RC1015 | Microsoft Docs"
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
  - "RC1015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1015"
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器错误 RC1015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法打开包含文件“filename”  
  
 给定包含文件不存在、未能打开或者没有找到。  
  
 确保环境设置有效并且已指定此文件的正确路径。  确保资源编译器有足够的文件句柄可用。  如果文件位于网络驱动器上，请确保您有打开此文件的权限。  
  
 在“配置属性”\-\>“资源”\-\>“常规”属性页中可配置“附加包含目录”，即使包含文件存在于该“附加包含目录”所指出的目录中，也可能发生 RC1015；请指定包含文件的完整路径。  
  
 有关更多信息，请参见知识库文章 Q326987：RC1015 Error When Using Resource View If the Include Path is Too Long（在包含路径过长情况下使用资源视图时的 RC1015 错误）。