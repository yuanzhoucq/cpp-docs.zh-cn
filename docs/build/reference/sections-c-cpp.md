---
title: "SECTIONS (C/C++) | Microsoft Docs"
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
  - "SECTIONS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SECTIONS .def 文件语句"
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# SECTIONS (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

引入了一个由一个或多个 `definitions`（关于项目输出文件各节的访问说明符）组成的节。  
  
```  
SECTIONS  
definitions  
```  
  
## 备注  
 每个定义必须在单独一行上。  `SECTIONS` 关键字可以在第一个定义所在的同一行或前一行上。  .def 文件可以包含一个或多个 `SECTIONS` 语句。  
  
 该 `SECTIONS` 语句为图像文件中的一节或多节设置特性，并可用于重写每种节类型的默认特性。  
  
 `definitions` 的格式为：  
  
 `.section_name specifier`  
  
 此处，`.section_name` 为程序图像中的节名， `specifier`为下列一个或多个访问修饰符：  
  
|修饰符|说明|  
|---------|--------|  
|`EXECUTE`|节是可执行的|  
|`READ`|允许对数据进行读取操作|  
|`SHARED`|在所有加载图像的进程中共享节|  
|`WRITE`|允许对数据进行写操作|  
  
 用空格分开修饰符名。  例如：  
  
```  
SECTIONS  
.rdata READ WRITE  
```  
  
 `SECTIONS` 标记部分 `definitions` 列表的开头。  每个 `definition` 必须处于单独的一行。  `SECTIONS` 关键字可以和第一个 `definition` 关键字在同一行或在前一行。  .def 文件可以包含一个或多个 `SECTIONS` 语句。  `SEGMENTS` 关键字作为 `SECTIONS` 的同义词受到支持。  
  
 Visual C\+\+ 的早期版本支持：  
  
```  
section [CLASS 'classname'] specifier  
```  
  
 出于兼容性考虑，支持 `CLASS` 关键字，但忽略了它。  
  
 另一种指定节特性的方法是使用 [\/SECTION](../../build/reference/section-specify-section-attributes.md) 选项。  
  
## 请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)