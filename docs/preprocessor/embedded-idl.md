---
title: "embedded_idl | Microsoft Docs"
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
  - "embedded_idl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "embedded_idl 特性"
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# embedded_idl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 指定将类型库写入保留了特性生成的代码的 .tlh 文件。  
  
## 语法  
  
```  
embedded_idl[("param")]  
```  
  
#### 参数  
 `param`  
 可以是以下两个值之一：  
  
-   emitidl：从类型库导入的类型信息将出现在为特性化项目生成的 IDL 中。如果不为 `embedded_idl` 指定参数，则这是默认值，并将有效。  
  
-   no\_emitidl：从类型库导入的类型信息将不出现在为特性化项目生成的 IDL 中。  
  
## 示例  
  
```  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## 备注  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)