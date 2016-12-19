---
title: "_finite _finitef | Microsoft Docs"
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
  - "_finite"
  - "_finitef"
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
  - "finite"
  - "_finite"
  - "_finitef"
  - "math/_finite"
  - "math/_finitef"
  - "float/_finite"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "finite 函数"
  - "_finite 函数"
  - "_finitef 函数"
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _finite _finitef
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定浮点值是否是有限的。  
  
## 语法  
  
```  
int _finite(   
   double x   
);  
  
int _finitef(   
   float x   
); /* x64 and ARM/ARM64 only */  
```  
  
#### 参数  
 `x`  
 要测试的浮点值。  
  
## 返回值  
 如果参数 *x* 是有限值，则 `_finite` 和 `_finitef` 均返回非零值；也即如果 – INF \< `x` \< \+ INF。 如果该自变量为无限值或为 NAN，则其返回 0。  
  
## 备注  
 `_finite` 和 `_finitef` 函数是 Microsoft 专用。`_finitef` 函数只是平台为 x86、 ARM、 或 ARM64 编译时可用。  
  
## 要求  
  
|函数|必需的标头 \(C\)|必需的标头 \(C\+\+\)|  
|--------|-----------------|---------------------|  
|`_finite`|\<float.h\> 或 \<math.h\>|\<float.h\>、\<math.h\>、\<cfloat\> 或 \<cmath\>|  
|`_finitef`|\<math.h\>|\<math.h\> 或 \<cmath\>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Double::IsInfinity](https://msdn.microsoft.com/en-us/library/system.double.isinfinity.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [isnan，\_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [\_fpclass \_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)