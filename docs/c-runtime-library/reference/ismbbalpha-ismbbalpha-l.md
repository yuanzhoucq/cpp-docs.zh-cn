---
title: "_ismbbalpha、_ismbbalpha_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbbalpha"
  - "_ismbbalpha_l"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "ismbbalpha"
  - "ismbbalpha_l"
  - "_ismbbalpha"
  - "_ismbbalpha_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ismbbalpha 函数"
  - "ismbbalpha_l 函数"
  - "_ismbbalpha 函数"
  - "_ismbbalpha_l 函数"
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _ismbbalpha、_ismbbalpha_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定指定的多字节字符是否是字母。  
  
## 语法  
  
```  
int _ismbbalpha(  
   unsigned int c   
);  
int _ismbbalpha_l(  
   unsigned int c   
);  
```  
  
#### 参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果表达式满足以下条件，则 `_ismbbalpha` 返回非零值：  
  
```  
isalpha || _ismbbkalnum  
```  
  
 对于 `c` 是非零，否则是 0。`_ismbbalpha` 对与区域设置相关的所有字符设置使用当前区域设置。`_ismbbalpha_l` 具有相同的效果，只不过它使用已传入的区域设置。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ismbbalpha`|\<mbctype.h\>|  
|`_ismbbalpha_l`|\<mbctype.h\>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)