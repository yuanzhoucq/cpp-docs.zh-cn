---
title: "_ismbbblank、_ismbbblank_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbbblank_l"
  - "_ismbbblank"
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
dev_langs: 
  - "C++"
ms.assetid: d21b2e41-7206-41f5-85bb-9c9ab4f3e21b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _ismbbblank、_ismbbblank_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定指定的多节字符是否为空字符。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _ismbbblank(  
   unsigned int c   
);  
int _ismbbblank_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果 `c` 表示空格字符 \(0x20\)、水平制表符 \(0x09\) 或用于分隔 `isspace` 为真的文本行内的字的区域设置特定字符，`_ismbbblank` 返回非零值；否则，返回 0。  `_ismbbblank` 对与区域设置相关的所有行为使用当前区域设置。  `_ismbbblank_l` 相同，除非改为使用传递的区域设置。  有关详细信息，请参阅 [区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ismbbblank`|\<mbctype.h\>|  
|`_ismbbblank_l`|\<mbctype.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)