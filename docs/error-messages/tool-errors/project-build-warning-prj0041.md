---
title: "项目生成警告 PRJ0041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0041"
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 项目生成警告 PRJ0041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未找到缺少的依赖项“dependency”，属于文件“file”。您的项目仍然可以生成，但是在找到此文件之前，它可能会一直显示为已过期。  
  
 一个文件（例如资源文件或 .idl\/.odl 文件）包含了项目系统未能解析的 include 语句。  
  
 因为项目系统不处理预处理器语句（例如 \#if），所以，有问题的语句可能实际上不是该生成的一部分。  
  
 若要解决此警告，请删除 .rc 文件中所有不需要的代码或添加适当名称的占位符文件。