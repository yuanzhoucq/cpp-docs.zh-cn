---
title: "srand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "srand"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "srand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数字, 伪随机"
  - "数字, 随机"
  - "伪随机数"
  - "随机数, 生成"
  - "随机起点"
  - "随机起点, 设置"
  - "srand 函数"
  - "起点"
  - "起点, 设置随机"
ms.assetid: 7bf56dc5-5692-4182-a3c1-18af98d2dd1a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# srand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置伪随机数字生成器的起始种子值。  
  
## 语法  
  
```  
void srand(  
   unsigned int seed   
);  
```  
  
#### 参数  
 `seed`  
 伪随机数字的种子生成  
  
## 备注  
 `srand` 函数在当前线程中设置生成一系列伪随机整数的起点。  若要重新初始化生成器来创建顺序相同的结果，请调用 `srand` 函数并再次使用同一 `seed` 参数。  `seed` 的其他值将设置生成器到伪随机数序列中的不同起点。  `rand` 检索生成的伪随机数字。  在调用任何`srand`之前调用 `rand`，与调用`srand` 和 `seed` 会产生和1一样的序列。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`srand`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [rand](../../c-runtime-library/reference/rand.md) 的示例。  
  
## .NET Framework 等效项  
 [系统唯一的类](https://msdn.microsoft.com/en-us/library/system.random.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [rand](../../c-runtime-library/reference/rand.md)