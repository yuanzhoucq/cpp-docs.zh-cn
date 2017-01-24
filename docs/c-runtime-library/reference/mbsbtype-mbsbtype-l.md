---
title: "_mbsbtype、_mbsbtype_l | Microsoft Docs"
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
  - "_mbsbtype_l"
  - "_mbsbtype"
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
  - "mbsbtype"
  - "mbsbtype_l"
  - "_mbsbtype_l"
  - "_mbsbtype"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsbtype 函数"
  - "_mbsbtype_l 函数"
  - "mbsbtype 函数"
  - "mbsbtype_l 函数"
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsbtype、_mbsbtype_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回字节的类型在字符串中。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _mbsbtype(  
   const unsigned char *mbstr,  
   size_t count   
);  
int _mbsbtype_l(  
   const unsigned char *mbstr,  
   size_t count,  
   _locale_t locale   
);  
```  
  
#### 参数  
 `mbstr`  
 多字节字符序列的地址。  
  
 `count`  
 从字符串的开头的偏移量。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 `_mbsbtype` 和 `_mbsbtype_l`返回在指定的字节指示测试结果的整数值。  清单常数在下表中 Mbctype.h 定义。  
  
|返回值|字节类型|  
|---------|----------|  
|`_MBC_SINGLE` \(0\)|单字节字符。  例如，在代码页 932，`_mbsbtype` 返回 0;如果指定的字节在范围内 0x20 – 0x7E 或 0xA1 – 0xDF。|  
|`_MBC_LEAD` \(1\)|多字节字符中的前导字节。  例如，在代码页 932，`_mbsbtype` 返回 1;如果指定的字节范围在 0x81 中– 0x9F 或 0xE0 – 0xFC。|  
|`_MBC_TRAIL` \(2\)|多字节字符的尾随字节。  例如，在代码页 932，`_mbsbtype` 返回 2;如果指定的字节在范围内0x40 – 0x7E或0x80 – 0xFC.|  
|`_MBC_ILLEGAL` \(–1\)|`NULL` 字符串、无效字符或者在`mbstr`中的`count`偏移字节之前找到的`NULL`字节。|  
  
## 备注  
 `_mbsbtype` 函数确定在多字节字符串中的字节类型。  函数只检查该字节在 `mbstr`的偏移量 `count`，忽略在指定字节之前的无效字符。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果输入字符为`NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`_MBC_ILLEGAL`。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_mbsbtype`|\<mbstring.h\>|\<mbctype.h\>\*|  
|`_mbsbtype_l`|\<mbstring.h\>|\<mbctype.h\>\*|  
  
 \*要使用的清单常数返回值。  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用，就请参见 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。  
  
## 请参阅  
 [字节分类](../../c-runtime-library/byte-classification.md)