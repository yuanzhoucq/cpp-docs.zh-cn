---
title: "针对浮点常量的限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "常量, 浮点"
  - "FLOAT.H 头文件"
  - "浮点常量, 限制"
  - "浮点数字, 浮点限制"
  - "限制, 浮点常量"
  - "范围, 浮点常量"
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 针对浮点常量的限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 下表中提供了对浮点常量值的限制。  头文件 FLOAT.H 包含此信息。  
  
### 对浮点常量的限制  
  
|常量|含义|值|  
|--------|--------|-------|  
|**FLT\_DIGDBL\_DIGLDBL\_DIG**|位数 *q*，以便带有 *q* 小数位数的浮点数可以舍入为浮点表示形式并可以恢复原样而不会丢失精度。|6 15 15|  
|**FLT\_EPSILONDBL\_EPSILONLDBL\_EPSILON**|最小正数 *x*，以便 *x* \+ 1.0 不等于 1.0。|1.192092896e–07F 2.2204460492503131e–016 2.2204460492503131e–016|  
|**FLT\_GUARD**||0|  
|**FLT\_MANT\_DIGDBL\_MANT\_DIGLDBL\_MANT\_DIG**|由在浮点有效位数中的 **FLT\_RADIX** 指定的基数中的位数。  基数为 2；因此这些值指定位。|24 53 53|  
|**FLT\_MAXDBL\_MAXLDBL\_MAX**|可表示的最大浮点数。|3.402823466e\+38F 1.7976931348623158e\+308 1.7976931348623158e\+308|  
|**FLT\_MAX\_10\_EXPDBL\_MAX\_10\_EXPLDBL\_MAX\_10\_EXP**|最大整数，以便 10 的该数字的幂是一个可表示的浮点数。|38 308 308|  
|**FLT\_MAX\_EXPDBL\_MAX\_EXPLDBL\_MAX\_EXP**|最大整数，以便 **FLT\_RADIX** 的该数字的幂是一个可表示的浮点数。|128 1024 1024|  
|**FLT\_MINDBL\_MINLDBL\_MIN**|最小正值。|1.175494351e–38F 2.2250738585072014e–308 2.2250738585072014e–308|  
|**FLT\_MIN\_10\_EXPDBL\_MIN\_10\_EXPLDBL\_MIN\_10\_EXP**|最小负整数，以便 10 的该数字的幂是一个可表示的浮点数。|–37<br /><br /> –307<br /><br /> –307|  
|**FLT\_MIN\_EXPDBL\_MIN\_EXPLDBL\_MIN\_EXP**|最小负整数，以便 **FLT\_RADIX** 的该数字的幂是一个可表示的浮点数。|–125<br /><br /> –1021<br /><br /> –1021|  
|**FLT\_NORMALIZE**||0|  
|**FLT\_RADIX\_DBL\_RADIX\_LDBL\_RADIX**|基数的指数表示形式。|2 2 2|  
|**FLT\_ROUNDS\_DBL\_ROUNDS\_LDBL\_ROUNDS**|浮点加法的舍入模式。|1 \(near\) 1 \(near\) 1 \(near\)|  
  
 请注意，上表中的信息可能在未来的实现中不同。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [C 浮点常量](../c-language/c-floating-point-constants.md)