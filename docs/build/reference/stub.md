---
title: "STUB | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STUB"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STUB .def 文件语句"
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# STUB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当用于生成虚拟设备驱动程序 \(VxD\) 的模块定义文件时，STUB 允许指定包含将在 VxD 中使用的 IMAGE\_DOS\_HEADER 结构（在 WINNT.H 中定义）而不是默认头的文件名。  
  
```  
STUB:filename  
```  
  
## 备注  
 另一种指定 *filename* 的方法是使用 [\/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) 链接器选项。  
  
 在模块定义文件中，STUB 仅在生成 VxD 时有效。  
  
## 请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)