---
title: "编译器警告（等级 4）C4639 | Microsoft Docs"
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
  - "C4639"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4639"
ms.assetid: f94f7392-cdbb-4bf4-8a00-20dc90d3efe9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4639
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MSXML 错误，将不会处理 XML 文档注释。原因  
  
 此警告出现的原因有很多。  
  
 解决此警告的方法是：  
  
-   重新编译。  
  
-   通过重新安装公共语言运行时来重新安装 MSXML。  
  
-   编辑或移除导致该警告的文档注释，并重新进行编译。  
  
 发出 C4639 警告时，所有将来的 XML 注释处理都将禁用，并且不会生成 .xdc 文件。