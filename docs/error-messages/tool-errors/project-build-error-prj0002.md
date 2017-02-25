---
title: "项目生成错误 PRJ0002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0002"
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 项目生成错误 PRJ0002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从“command line”返回的结果有误。  
  
 由**“属性页”**对话框中的用户输入形成的命令 ***command line*** 返回了一个错误代码，但输出窗口中不显示任何信息。  
  
 该错误的解决取决于产生错误的工具。  对于 MIDL，如果定义了 \/o（重定向输出），则对错误出处了然在胸。  
  
 批处理文件（如自定义生成步骤或生成事件）对失败情况没有提示性信息，也可能是导致该错误的原因。