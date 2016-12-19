---
title: "编译器警告（等级 3）C4192 | Microsoft Docs"
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
  - "C4192"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4192"
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4192
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

导入类型库“library”时自动排除“name”  
  
 `#import` 库包含一个 *name* 项，在 Win32 系统头中也定义了该项。  由于类型库的限制，**IUnknown** 或 GUID 等名称通常在类型库中定义，同时从系统头文件中复制定义。  `#import` 将检测这些项，并且拒绝将这些项合并到 .tlh 和 .tli 头文件中。  
  
 若要重写此行为，请使用 `#import` 特性 [no\_auto\_exclude](../../preprocessor/no-auto-exclude.md) 和 [include\(\)](../../preprocessor/include-parens.md)。