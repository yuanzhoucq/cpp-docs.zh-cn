---
title: "浮点限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FLOAT.H 头文件"
  - "浮点常量, 限制"
  - "浮点数字, 浮点限制"
  - "限制, 浮点常量"
  - "范围, 浮点常量"
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 浮点限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 下表列出了浮点常数的值的限制。  标准头文件 FLOAT.H 中也定义了这些限制。  
  
### 对浮点常量的限制  
  
|常量|含义|值|  
|--------|--------|-------|  
|FLT\_DIG DBL\_DIG LDBL\_DIG|位数 q，以便 q 十进制数的浮点数可以被舍入到浮点表示形式并返回，而不会丢失精度。|6 15 15|  
|FLT\_EPSILON DBL\_EPSILON LDBL\_EPSILON|最小正数 x，以便 x \+ 1.0 不等于 1.0。|1.192092896e–07F 2.2204460492503131e–016 2.2204460492503131e–016|  
|FLT\_GUARD||0|  
|FLT\_MANT\_DIG DBL\_MANT\_DIG LDBL\_MANT\_DIG|由浮点有效位数中的 FLT\_RADIX 指定的基数中的位数。  该基数为 2；因此，这些值指定位。|24 53 53|  
|FLT\_MAX DBL\_MAX LDBL\_MAX|可表示的最大浮点数。|3.402823466e\+38F 1.7976931348623158e\+308 1.7976931348623158e\+308|  
|FLT\_MAX\_10\_EXP DBL\_MAX\_10\_EXP LDBL\_MAX\_10\_EXP|最大整数，以便 10 的该数字的幂是一个可表示的浮点数。|38 308 308|  
|FLT\_MAX\_EXP DBL\_MAX\_EXP LDBL\_MAX\_EXP|最大整数，以便 FLT\_RADIX 的该数字的幂是一个可表示的浮点数。|128 1024 1024|  
|FLT\_MIN DBL\_MIN LDBL\_MIN|最小正值。|1.175494351e–38F 2.2250738585072014e–308 2.2250738585072014e–308|  
|FLT\_MIN\_10\_EXP DBL\_MIN\_10\_EXP LDBL\_MIN\_10\_EXP|最小负整数，以便 10 的该数字的幂是一个可表示的浮点数。|–37<br /><br /> –307<br /><br /> –307|  
|FLT\_MIN\_EXP DBL\_MIN\_EXP LDBL\_MIN\_EXP|最小负整数，以便 FLT\_RADIX 的该数字的幂是一个可表示的浮点数。|–125<br /><br /> –1021<br /><br /> –1021|  
|FLT\_NORMALIZE||0|  
|FLT\_RADIX \_DBL\_RADIX \_LDBL\_RADIX|基数的指数表示形式。|2 2 2|  
|FLT\_ROUNDS \_DBL\_ROUNDS \_LDBL\_ROUNDS|浮点添加的舍入模式。|1 \(near\) 1 \(near\) 1 \(near\)|  
  
> [!NOTE]
>  表中信息可能与该产品的将来版本不同。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [整数限制](../cpp/integer-limits.md)