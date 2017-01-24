---
title: "项目生成警告 PRJ0029 | Microsoft Docs"
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
  - "PRJ0029"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0029"
ms.assetid: f02c09c6-09f3-4d44-8cd4-9a25336be1ea
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成警告 PRJ0029
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未设置项目级自定义生成步骤的“输出”属性。将跳过自定义生成步骤。  
  
 由于未指定输出，因此未执行自定义生成步骤。  
  
 若要解决该错误，请执行以下操作之一：  
  
-   从生成中排除自定义生成步骤。  
  
-   添加输出。  
  
-   删除自定义生成步骤中的命令内容。