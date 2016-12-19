---
title: "raw_dispinterfaces | Microsoft Docs"
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
  - "raw_dispinterfaces"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "raw_dispinterfaces 特性"
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raw_dispinterfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 告知编译器生成低级别的调度接口方法的包装器函数和调用 **IDispatch::Invoke** 并返回 `HRESULT` 错误代码的属性。  
  
## 语法  
  
```  
raw_dispinterfaces  
```  
  
## 备注  
 如果未指定该特性，则只生成高级包装器，它在失败时引发 C\+\+ 异常。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)