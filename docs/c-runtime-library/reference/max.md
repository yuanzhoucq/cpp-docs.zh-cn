---
title: "__max | Microsoft Docs"
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
  - "__max"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "max"
  - "__max"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__max 宏"
  - "max 宏"
  - "maximum 宏"
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __max
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回两个值中的较大者。  
  
## 语法  
  
```  
type __max(  
   type a,  
   type b   
);  
```  
  
#### 参数  
 `type`  
 任何数字数据类型。  
  
 `a, b`  
 任何数值类型的值会被比较。  
  
## 返回值  
 `__max` 返回参数中较大的。  
  
## 备注  
 `__max` 宏对两个值进行比较并返回值较大的一个。  参数可以是任何数字数据类型，有符号或者没有符号。  参数和返回值必须是同一数据类型。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`__max`|\<stdlib.h\>|  
  
## 示例  
 有关更多信息，请参见[\_\_min](../../c-runtime-library/reference/min.md)中的例子。  
  
## .NET Framework 等效项  
 [System::Math::Max](https://msdn.microsoft.com/en-us/library/system.math.max.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_\_min](../../c-runtime-library/reference/min.md)