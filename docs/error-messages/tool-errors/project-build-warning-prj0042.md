---
title: "项目生成警告 PRJ0042 | Microsoft Docs"
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
  - "PRJ0042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0042"
ms.assetid: 682c9999-6f85-409f-b102-00c93243f74f
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成警告 PRJ0042
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未设置**文件“*file*”的自定义生成步骤的“输出”属性。将跳过自定义生成步骤。**  
  
 由于未指定输出，因此未执行自定义生成步骤。  
  
 若要解决该错误，请执行以下操作之一：  
  
-   从生成中排除自定义生成步骤。  
  
-   添加输出。  
  
-   删除自定义生成步骤中的命令内容。