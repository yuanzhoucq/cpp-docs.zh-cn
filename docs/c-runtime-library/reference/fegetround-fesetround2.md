---
title: "fegetround、fesetround | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fegetround"
  - "fesetround"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fegetround"
  - "fesetround"
  - "fenv/fegetround"
  - "fenv/fesetround"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fegetround 函数"
  - "fesetround 函数"
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fegetround、fesetround
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取或设置当前的浮点舍入模式。  
  
## 语法  
  
```  
int fegetround(void);  
  
int fesetround(  
   int round_mode  
);   
```  
  
#### 参数  
 `round_mode`  
 要作为其中一个浮点舍入宏设置的舍入模式。 如果该值不等于其中一个浮点舍入宏，则舍入模式不会更改。  
  
## 返回值  
 如果成功，则 `fegetround` 返回作为其中一个浮点舍入宏值的舍入模式。 如果无法确定当前的舍入模式，它返回一个负值。  
  
 如果成功，`fesetround` 返回 0。 否则，返回一个非零值。  
  
## 备注  
 浮点运算可以使用数种舍入模式中的其中一种。 这些模式控制存储结果时浮点运算结果的舍入方向。 以下是在 \<fenv.h\> 中定义的浮点舍入宏的名称和行为：  
  
|宏|描述|  
|-------|--------|  
|FE\_DOWNWARD|向负无穷舍入。|  
|FE\_TONEAREST|向最近一方舍入。|  
|FE\_TOWARDZERO|向零舍入。|  
|FE\_UPWARD|向正无穷舍入。|  
  
 FE\_TONEAREST 的默认行为是要将结果从可表示值的中间向具有偶数 \(0\) 最低有效位的最近值舍入。  
  
 当前舍入模式将影响以下操作：  
  
-   字符串转换  
  
-   常量表达式之外的浮点算术运算符的结果。  
  
-   库舍入函数，如 `rint` 和 `nearbyint`。  
  
-   从标准库的数学函数返回的值。  
  
 当前舍入模式不影响以下操作：  
  
-   `trunc`、`ceil`、`floor` 和 `lround` 库函数。  
  
-   浮点到整数隐式强制转换和转换，始终向零舍入。  
  
-   常量表达式中浮点算术运算符的结果，始终舍入到最接近的值。  
  
 若要使用这些函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`fegetround`, `fesetround`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [nearbyint、 nearbyintf、 nearbyintl](../../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)   
 [rint, rintf, rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)   
 [lrint、 lrintf、 lrintl、 llrint、 llrintf、 llrintl](../../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)