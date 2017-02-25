---
title: "tlbid | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tlbid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tlbid 特性"
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# tlbid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 允许加载主类型库之外的库。  
  
## 语法  
  
```  
tlbid(number)  
```  
  
#### 参数  
 `number`  
 `filename` 中的类型库的编号。  
  
## 备注  
 如果将多个类型库内置于一个 DLL，则可以使用 `tlbid` 来加载非主类型库。  
  
 例如：  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 等效于：  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)