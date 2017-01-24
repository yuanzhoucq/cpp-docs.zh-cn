---
title: "__RTDynamicCast | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__RTDynamicCast"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__RTDynamicCast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__RTDynamicCast"
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __RTDynamicCast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[dynamic\_cast](../cpp/dynamic-cast-operator.md) 运算符的运行时实现。  
  
## 语法  
  
```cpp  
PVOID __RTDynamicCast (  
   PVOID inptr,   
   LONG VfDelta,  
   PVOID SrcType,  
   PVOID TargetType,   
   BOOL isReference  
   ) throw(...)  
```  
  
#### 参数  
 `inptr`  
 一个指向多态对象的指针。  
  
 `VfDelta`  
 对象中的虚函数指针的偏移。  
  
 `SrcType`  
 `inptr` 参数指向静态类型对象。  
  
 `TargetType`  
 转换的预期结果。  
  
 `isReference`  
 如果输入是引用，为`true`；如果输入为指针，为`false`。  
  
## 返回值  
 如果成功，为适当的子对象的指针，否则，为NULL。  
  
## 异常  
 `bad_cast()` 如果`dynamic_cast<>` 的输入是引用并且转换失败。  
  
## 备注  
 将 `inptr` 转换为 `TargetType`的对象类型。  如果 `TargetType` 是指针，则`inptr` 的类型必须是指针，如果 `TargetType` 是引用，则为左值。  `TargetType` 必须是一个指针或是以前定义的类类型的引用或指向 void 的指针。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_\_RTDynamicCast|rtti.h|