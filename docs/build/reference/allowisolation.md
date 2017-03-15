---
title: "/ALLOWISOLATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ALLOWISOLATION"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALLOWISOLATION editbin 选项"
  - "ALLOWISOLATION editbin 选项"
  - "-ALLOWISOLATION editbin 选项"
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /ALLOWISOLATION
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定清单查找的行为。  
  
## 语法  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## 备注  
 **\/ALLOWISOLATION** 将导致操作系统进行清单查找和加载。  
  
 默认为 **\/ALLOWISOLATION**。  
  
 **\/ALLOWISOLATION:NO** 指示像没有清单一样加载可执行文件，并导致 [EDITBIN 参考](../../build/reference/editbin-reference.md) 在可选标头的 `DllCharacteristics` 字段中设置 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 位。  
  
 当对可执行文件禁用隔离时，Windows 加载程序不会尝试为新创建的进程查找应用程序清单。  新进程没有默认激活上下文，即使可执行文件本身中有清单或存在名为 *executable\-name*.exe.manifest 的清单。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [\/ALLOWISOLATION（清单查找）](../../build/reference/allowisolation-manifest-lookup.md)   
 [清单文件引用](http://msdn.microsoft.com/library/aa375632.aspx)