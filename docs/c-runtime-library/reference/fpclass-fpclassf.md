---
title: "_fpclass _fpclassf | Microsoft Docs"
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
  - "_fpclass"
  - "_fpclassf"
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
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fpclass"
  - "_fpclass"
  - "_fpclassf"
  - "math/_fpclass"
  - "float/_fpclass"
  - "math/_fpclassf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fpclass 函数"
  - "浮点数，IEEE 表示形式"
  - "_fpclass 函数"
  - "_fpclassf 函数"
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fpclass _fpclassf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回一个值，该值指示参数的浮点分类。  
  
## 语法  
  
```  
int _fpclass(   
   double x   
);  
  
int _fpclassf(   
   float x   
); /* x64 only */  
```  
  
#### 参数  
 `x`  
 要测试的浮点值。  
  
## 返回值  
 `_fpclass` 和 `_fpclassf` 函数返回一个整数值，该值指示参数的浮点分类 `x`。 分类可能具有 \<.h \> 中定义的以下值之一。  
  
|值|描述|  
|-------|--------|  
|`_FPCLASS_SNAN`|信令 NaN|  
|`_FPCLASS_QNAN`|静默 NaN|  
|`_FPCLASS_NINF`|负无穷大 \( –INF\)|  
|`_FPCLASS_NN`|标准化的非零负值|  
|`_FPCLASS_ND`|非标准化的负值|  
|`_FPCLASS_NZ`|负零 \( – 0\)|  
|`_FPCLASS_PZ`|正零 \(\+0\)|  
|`_FPCLASS_PD`|非标准化的正值|  
|`_FPCLASS_PN`|标准化的非零正值|  
|`_FPCLASS_PINF`|正无穷大 \(\+INF\)|  
  
## 备注  
 `_fpclass` 和 `_fpclassf` 函数是 Microsoft 专用。 闭包类似于 [fpclassify](../../c-runtime-library/reference/fpclassify.md), ，但返回有关参数的更多详情。`_fpclassf` 函数只是在针对 x64 编译时可用的平台。  
  
## 要求  
  
|函数|必需的标头|  
|--------|-----------|  
|`_fpclass`|\<float.h\>|  
  
 有关兼容性和符合性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [isnan，\_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [fpclassify](../../c-runtime-library/reference/fpclassify.md)