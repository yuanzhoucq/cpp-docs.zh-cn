---
title: "VERSION (C/C++) | Microsoft Docs"
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
  - "VERSION"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VERSION .def 文件语句"
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# VERSION (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通知 LINK 将一个数字放到 .exe 文件或 DLL 的头中。  
  
```  
VERSION major[.minor]  
```  
  
## 备注  
 *major* 和 *minor* 参数为 0 到 65,535 范围之间的十进制数。  默认值为版本 0.0。  
  
 另一种指定版本号的方法是使用[版本信息](../../build/reference/version-version-information.md) \(\/VERSION\) 选项。  
  
## 请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)