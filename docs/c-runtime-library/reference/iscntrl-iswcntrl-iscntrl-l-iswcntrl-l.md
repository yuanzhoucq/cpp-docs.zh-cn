---
title: "iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l | Microsoft Docs"
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
  - "iscntrl"
  - "_iswcntrl_l"
  - "_iscntrl_l"
  - "iswcntrl"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_istcntrl_l"
  - "_iswcntrl_l"
  - "iswcntrl"
  - "_iscntrl_l"
  - "iscntrl"
  - "_istcntrl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_iscntrl_l 函数"
  - "_istcntrl 函数"
  - "_istcntrl_l 函数"
  - "_iswcntrl_l 函数"
  - "iscntrl 函数"
  - "istcntrl 函数"
  - "iswcntrl 函数"
ms.assetid: 616eebf9-aed4-49ba-ba2c-8677c8fe6fb5
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示控制字符。  
  
## 语法  
  
```  
int iscntrl(   
   int c   
);  
int iswcntrl(   
   wint_t c   
);  
int _iscntrl_l(   
   int c,  
   _locale_t locale  
);  
int _iswcntrl_l(   
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要测试的整数  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果 `c` 是可打印字母的特定表示，则每个实例返回非零值。  `iscntrl` 返回一个非零值，如果 `c` 是控制字符 \(0x00 – 0x1F 或 0x7F\)。  如果 `c` 是控件宽字符，`iswcntrl` 返回一个非零值。  如果 `c` 不满足测试条件，则每个实例都返回0。  
  
 这些带有 `_l` 后缀的函数使用传递的区域设置参数而不是当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果`c` 不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），`iscntrl`和`_iscntrl_l`的行为是未定义的。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istcntrl`|`iscntrl`|`iscntrl`|`iswcntrl`|  
|`_istcntrl_l`|`_iscntrl_l`|`_iscntrl_l`|`_iswcntrl_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`iscntrl`|\<ctype.h\>|  
|`iswcntrl`|\<ctype.h\> 或 \<wchar.h\>|  
|`_iscntrl_l`|\<ctype.h\>|  
|`_iswcntrl_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Char::IsControl](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)