---
title: "mbrtoc16, mbrtoc32 | Microsoft Docs"
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
  - "mbrtoc16"
  - "mbrtoc32"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbrtoc16"
  - "mbrtoc32"
  - "uchar/mbrtoc16"
  - "uchar/mbrtoc32"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "mbrtoc16 函数"
  - "mbrtoc32 函数"
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mbrtoc16, mbrtoc32
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将窄字符串的首个多字节字符转换为等效的 UTF\-16 或 UTF\-32 字符。  
  
## 语法  
  
```  
size_t mbrtoc16(   
   char16_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
size_t mbrtoc32(  
   char32_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
```  
  
#### 参数  
 `destination`  
 指向与要转换的多字节字符等效的 `char16_t` 或 `char32_t` 的指针。 如果为 null，则该函数不存储值。  
  
 `source`  
 指向要转换的多字节字符串的指针。  
  
 `max_bytes`  
 存储在 `source` 中用于测试转换字符的最大字节数。 它应是介于 1 到 `source` 中的剩余字节数之间的值（包括任何 null 终止符）。  
  
 `state`  
 指向用于将多字节字符串解释为一个或多个输出字符的 `mbstate_t` 转换状态对象。  
  
## 返回值  
 如果成功，返回第一个适用条件的值，假定当前 `state` 值为：  
  
|值|条件|  
|-------|--------|  
|0|下一个从 `source` 转换的 `max_bytes` 或者较少字符与 null 宽字符对应，该字符是 `destination` 不为 null 时存储的值。<br /><br /> `state` 包含初始位移状态。|  
|介于 1 和 `max_bytes` 之间（包括这两个值）|返回的值是填充有效多字节字符的 `source` 的字节数。 如果 `destination` 不为 null，将存储转换后的宽字符。|  
|\-3|如果 `destination` 不为 null，则通过上次函数调用生成的下一个宽字符存储在 `destination` 中。 此次函数调用不会使用 `source` 中的字节。<br /><br /> 当 `source` 指向需要用多个宽字符表示的多字节字符（例如代理项对）时，则会更新 `state` 值，以便下一个函数调用写出其他字符。|  
|\-2|下一个 `max_bytes` 字节表示不完整但可能有效的多字节字符。`destination` 中不存储任何值。 如果 `max_bytes` 为 0，会出现此结果。|  
|\-1|发生编码错误。 下一个 `max_bytes` 或更少字节数不有利于实现完整且有效的多字节字符。`destination` 中不存储任何值。<br /><br /> `EILSEQ` 存储在 `errno` 中，未指定转化状态 `state`|  
  
## 备注  
 `mbrtoc16` 函数最多可从 `source` 中读取 `max_bytes` 个字节，以查找第一个完整有效的多字节字符，然后将等效的 UTF\-16 字符存储在 `destination` 中。 根据当前线程多字节区域设置解释源字节。 如果多字节字符需要多个 UTF 16 输出字符，如代理项对，则 `state` 值被设置为在下一次调用 `mbrtoc16` 时将下一个 UTF\-16 字符存储在 `destination` 中。`mbrtoc32` 函数完全相同，但输出存储为 UTF\-32 字符。  
  
 如果 `source` 为 null，这些函数将返回使用 `destination`的 `NULL`、`source`的 `""` 和 `max_bytes` 的 `1` 参数进行调用的等效项。 传递的值 `destination` 和 `max_bytes` 将被忽略。  
  
 如果 `source` 函数不为 null，函数从字符串起始位置开始，最多检查 `max_bytes` 个字节，以确定填充下一个多字节字符（包括任何位移序列）所需的字节数。 如果检查的字节包含有效且完整的多字节字符，该函数将字符转换为等效的 16 位或 32 位宽字符或字符。 如果 `destination` 不为 null，该函数会在目标中存储第一个（并且可能是唯一的）结果字符。 如果需要其他输出字符，将在 `state` 中设置值，以便后续调用该函数时输出其他字符并返回 \-3 值。 如果不需要其他输出字符，则将 `state` 设置为初始位移状态。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`mbrtoc16`, `mbrtoc32`|\<uchar.h\>|\<cuchar\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [c16rtomb, c32rtomb](../../c-runtime-library/reference/c16rtomb-c32rtomb1.md)   
 [mbrtowc](../../c-runtime-library/reference/mbrtowc.md)   
 [mbsrtowcs](../../c-runtime-library/reference/mbsrtowcs.md)   
 [mbsrtowcs\_s](../../c-runtime-library/reference/mbsrtowcs-s.md)