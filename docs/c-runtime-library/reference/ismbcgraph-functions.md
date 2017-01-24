---
title: "_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbcpunct_l"
  - "_ismbcblank"
  - "_ismbcprint"
  - "_ismbcgraph_l"
  - "_ismbcblank_l"
  - "_ismbcpunct"
  - "_ismbcprint_l"
  - "_ismbcspace_l"
  - "_ismbcspace"
  - "_ismbcgraph"
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
  - "_ismbcspace"
  - "_ismbcgraph"
  - "_ismbcpunct"
  - "ismbcspace_l"
  - "ismbcgraph"
  - "_ismbcgraph_l"
  - "_ismbcprint"
  - "_ismbcspace_l"
  - "ismbcprint"
  - "ismbcgraph_l"
  - "ismbcspace"
  - "ismbcpunct"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbcgraph 函数"
  - "_ismbcgraph_l 函数"
  - "_ismbcprint 函数"
  - "_ismbcprint_l 函数"
  - "_ismbcpunct 函数"
  - "_ismbcpunct_l 函数"
  - "_ismbcspace 函数"
  - "_ismbcspace_l 函数"
  - "ismbcgraph 函数"
  - "ismbcgraph_l 函数"
  - "ismbcprint 函数"
  - "ismbcprint_l 函数"
  - "ismbcpunct 函数"
  - "ismbcpunct_l 函数"
  - "ismbcspace 函数"
  - "ismbcspace_l 函数"
ms.assetid: 8e0a5f47-ba64-4411-92a3-3c525d16e3be
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定字符是否为图形字符、显示字符、标点符号或空格字符。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关更多信息，请参见[CRT 函数不支持 \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int _ismbcgraph(  
   unsigned int c   
);  
int _ismbcgraph_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcprint(  
   unsigned int c   
);  
int _ismbcprint_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcpunct(  
   unsigned int c  
);  
int _ismbcpunct_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcblank(  
   unsigned int c   
);  
int _ismbcblank_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcspace(  
   unsigned int c   
);  
int _ismbcspace_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要确定的字符。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 每个程序在字符满足测试条件时返回一个非零值，在不满足测试条件时返回0。  如果`c` \<\= 255，且存在相应的 `_ismbb` 实例 \(例如，`_ismbcalnum` 对应于 `_ismbbalnum`\)，则结果是相应的`_ismbb`实例的返回值。  
  
 这些函数版本相同，只不过带有 `_l` 后缀的为区域设置相关行为使用区域设置通过而不是当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 备注  
 其中每个函数都针对给定的条件测试给定的多字节字符。  
  
|例程|测试条件|代码页 932 示例|  
|--------|----------|----------------|  
|`_ismbcgraph`|图形|当且仅当 `c` 是任何 ASCII 或片假名可打印字符（除空格（）外）的单字节表示时，返回非零。|  
|`_ismbcprint`|可打印|当且仅当 `c` 是任何 ASCII 或片假名可打印字符（包含空格（））的单字节表示时，返回非零。|  
|`_ismbcpunct`|标点|当且仅当 `c` 是任何 ASCII 或片假名标点符号的单字节表示形式时，返回非零。|  
|`_ismbcblank`|空格或水平制表符|当且仅当 `c` 是空格字符或水平制表符字符，返回一个非零值：`c`\=0x20 或 `c`\=0x09。|  
|`_ismbcspace`|空白|当且仅当 `c` 是空格时，返回非零值：`c`\=0x20 或 0x09\<\=`c`\<\=0x0D。|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ismbcgraph`|\<mbstring.h\>|  
|`_ismbcgraph_l`|\<mbstring.h\>|  
|`_ismbcprint`|\<mbstring.h\>|  
|`_ismbcprint_l`|\<mbstring.h\>|  
|`_ismbcpunct`|\<mbstring.h\>|  
|`_ismbcpunct_l`|\<mbstring.h\>|  
|`_ismbcblank`|\<mbstring.h\>|  
|`_ismbcblank_l`|\<mbstring.h\>|  
|`_ismbcspace`|\<mbstring.h\>|  
|`_ismbcspace_l`|\<mbstring.h\>|  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
  
-   [System::Char::IsPunctuation](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)  
  
-   [System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)  
  
-   对于 `_ismbcgraph` 和 `_ismbcprint`：不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_ismbc 例程](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 例程](../../c-runtime-library/ismbb-routines.md)