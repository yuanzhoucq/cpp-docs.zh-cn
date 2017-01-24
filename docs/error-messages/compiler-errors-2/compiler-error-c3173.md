---
title: "编译器错误 C3173 | Microsoft Docs"
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
  - "C3173"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3173"
ms.assetid: edf79e10-e8cf-4f76-8d33-ab9d05e974e9
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3173
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

idl 合并中的版本不匹配  
  
 当对象文件包含使用早期版本的编译器生成的嵌入 idl 时，将发生此错误。  编译器对版本号进行编码，以确保用于生成嵌入到 obj 文件中的 idl 内容的编译器，同时又是用于合并嵌入的 idl 的编译器。  
  
 更新 Visual C\+\+ 安装，使所有工具都是最新发布版本中的工具。