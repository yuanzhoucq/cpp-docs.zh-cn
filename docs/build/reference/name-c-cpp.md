---
title: "NAME (C/C++) | Microsoft Docs"
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
  - "name"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NAME .def 文件语句"
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NAME (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定主输出文件的名称。  
  
```  
NAME [application][BASE=address]  
```  
  
## 备注  
 另一种指定输出文件名的方法是使用 [\/OUT](../../build/reference/out-output-file-name.md) 链接器选项，而另一种设置基址的方法是使用 [\/BASE](../../build/reference/base-base-address.md) 链接器选项。  如果两种方法都指定了，则 \/OUT 重写 **NAME**。  
  
 如果生成 DLL，NAME 将只影响 DLL 名。  
  
## 请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)