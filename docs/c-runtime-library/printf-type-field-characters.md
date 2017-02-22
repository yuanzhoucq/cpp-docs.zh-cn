---
title: "printf 类型字段字符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "printf 函数, 格式规范字段"
  - "printf 函数, 类型字段字符"
ms.assetid: 699cb438-cd14-402e-9f81-c7a32acc3317
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# printf 类型字段字符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在格式规范中，`type` 字符是一个转换说明符，指定是否要将相应的参数解释为字符、字符串、指针、整数或浮点数。  `type` 字符是唯一所需的格式规范字段，它出现在任何可选字段之后。  
  
 根据相应的 `type` 字符和可选的[大小](../c-runtime-library/size-specification.md)前缀对紧跟格式字符串的参数进行解释。  通过使用 `c` 或 `C`，指定字符类型 `char` 和 `wchar_t` 的转换，通过使用 `s` 或 `S` 指定单字节和多字节或宽字符字符串，具体取决于正在使用的格式设置函数。  通过使用 `c` 和 `s` 指定的字符和字符串参数被 `printf` 系列函数解释为 `char` 和 `char*`，或被 `wprintf` 系列函数解释为 `wchar_t` 和 `wchar_t*`。  通过使用 `C` 和 `S` 指定的字符和字符串参数被 `printf` 系列函数解释为 `wchar_t` 和 `wchar_t*`，或被 `wprintf` 系列函数解释为 `char` 和 `char*`。  
  
 通过使用 `d`、`i`、`o`、`u`、`x` 和 `X` 指定整数类型（如 `short`、`int`、`long`、`long long`）以及其 `unsigned` 变体。  通过使用 `a`、`A`、`e`、`E`、`f`、`g` 和 `G` 指定浮点类型（如 `float`、`double` 和 `long double`）。  默认情况下，除非由 `size` 字段长度前缀进行修改，否则整型参数将被强制为 `int` 类型，浮点参数将被强制为 `double`。  在 64 位系统上，`int` 是 32 位的值；因此，确定 64 位整数的输出格式时，将把它截断，除非使用 `ll` 或 `I64` 的 `size` 前缀。  由 `p` 指定的指针类型使用平台的默认长度。  
  
> [!NOTE]
>  与 `printf` 和 `wprintf` 函数一起使用时，`C`、`S` 和 `Z` 类型字符以及 `c` 和 `s` 类型字符的行为是 Microsoft 扩展，与 ANSI 不兼容。  [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 不支持 `F` 类型字符。  
  
### printf 类型字段字符  
  
|类型字符|参数|输出格式|  
|----------|--------|----------|  
|`c`|字符|与 `printf` 函数一起使用时，指定单字节字符；与 `wprintf` 函数一起使用时，指定宽字符。|  
|`C`|字符|与 `printf` 函数一起使用时，指定宽字符；与 `wprintf` 函数一起使用时，指定单字节字符。|  
|`d`|Integer|带符号十进制整数。|  
|`i`|Integer|带符号十进制整数。|  
|`o`|Integer|无符号八进制整数。|  
|`u`|Integer|无符号十进制整数。|  
|`x`|Integer|无符号十六进制整数；使用“abcdef.”|  
|`X`|Integer|无符号十六进制整数；使用“ABCDEF.”|  
|`e`|浮点|有符号的值，形式为 \[ – \]`d`**.**`dddd` e \[*sign*\]`dd[d]`，其中 `d` 是一个十进制数，`dddd` 是一个或多个十进制数，`dd[d]` 是两三个十进制数，具体取决于[输出格式](../c-runtime-library/set-output-format.md)和指数大小，并且*符号*为 \+ 或 –。|  
|`E`|浮点|与 `e` 格式相同，除非 **E**（而非 **e**）引入了指数。|  
|`f`|浮点|有符号的值，形式为 \[ – \]`dddd`**.**`dddd`，其中 `dddd` 是一个或多个十进制数。  小数点前的数字位数取决于数字的度量值，小数点后的数字位数取决于所需精度。|  
|`g`|浮点|有符号的值显示为 `f` 或 `e` 格式，取其中对于给定的值和精度更为精简一个。  仅当值的指数小于 \-4 或大于等于 `precision` 参数时，使用 `e` 格式。  截去尾随零，仅当后跟一个或多个数字时，才会显示小数点。|  
|`G`|浮点|与 `g` 格式相同，除非 **E**（而非 **e**）引入指数（如果适用）。|  
|`a`|浮点|有符号十六进制双精度浮点值，形式为 \[−\]0x*h.hhhh* **p±**`dd`，其中 *h.hhhh* 是尾数的十六进制数（使用小写字母），`dd` 是指数的一个或多个数字。  精度指定此点后的数字位数。|  
|`A`|浮点|有符号十六进制双精度浮点值，形式为 \[−\]0X*h.hhhh* **P±**`dd`，其中 *h.hhhh* 是尾数的十六进制数（使用大写字母），`dd` 是指数的一个或多个数字。  精度指定此点后的数字位数。|  
|`n`|指向整数的指针|目前成功写入流或缓冲区的字符数。  此值存储在地址作为参数的整数中。  请参阅下文中的安全说明。|  
|`p`|指针类型|将参数显示为十六进制数中的地址。|  
|`s`|字符串|与 `printf` 函数一起使用时，指定单字节或多字节字符串；与 `wprintf` 函数一起使用时，指定宽字符字符串。  于第一个空字符之前或达到 `precision` 值之前，显示字符。|  
|`S`|字符串|与 `printf` 函数一起使用时，指定宽字符字符串；与 `wprintf` 函数一起使用时，指定单字节或多字节字符串。  于第一个空字符之前或达到 `precision` 值之前，显示字符。|  
|`Z`|`ANSI_STRING` 或 `UNICODE_STRING` 结构|当 [ANSI\_STRING](http://msdn.microsoft.com/library/windows/hardware/ff540605.aspx) 的地址或 [UNICODE\_STRING](http://msdn.microsoft.com/library/windows/hardware/ff564879.aspx) 结构作为参数传递时，显示包含在缓冲区中的字符串（此结构的 `Buffer` 字段指向此缓冲区）。  使用 `w` 的长度修饰符前缀指定 `UNICODE_STRING` 参数，例如 `%wZ`。  结构的 `Length` 字段必须设置为字符串的长度（以字节为单位）。  结构的 `MaximumLength` 字段必须设置为缓冲区的长度（以字节为单位）。<br /><br /> 通常情况下，`Z` 类型字符仅在使用格式规范（如 `dbgPrint` 和 `kdPrint`）的驱动程序调试函数中使用。|  
  
 如果对应浮点转换说明符的参数无限、不定或 NAN，则下表列出格式化输出。  
  
|值|输出|  
|-------|--------|  
|\+ 无穷|`1.#INF` *随机数字*|  
|– 无穷|`–1.#INF` *随机数字*|  
|不定（与静默 NaN 相同）|*数字* `.#IND` *随机数字*|  
|NAN|*数字* `.#NAN` *随机数字*|  
  
> [!NOTE]
>  如果与 `%Z` 对应的参数或与 `%s` 或 `%S` 对应的参数的 `Buffer` 字段为空指针，则将显示“\(null\)”。  
  
> [!NOTE]
>  在所有指数格式中，将显示的指数默认位数为三。  通过使用 [\_set\_output\_format](../c-runtime-library/set-output-format.md) 函数，可以将显示的数字位数设置为二；但如果指数大小要求，可扩展到三。  
  
> [!IMPORTANT]
>  `%n` 格式在本质上是不安全的，因此它默认处于禁用状态。  如果在格式字符串中遇到 `%n`，则调用无效的参数处理程序，如[参数验证](../c-runtime-library/parameter-validation.md)中所述。  若要启用 `%n` 支持，请参阅 [\_set\_printf\_count\_output](../c-runtime-library/reference/set-printf-count-output.md)。  
  
## 请参阅  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式规范语法：printf 和 wprintf 函数](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [标志指令](../c-runtime-library/flag-directives.md)   
 [printf 宽度规范](../c-runtime-library/printf-width-specification.md)   
 [精度规范](../c-runtime-library/precision-specification.md)   
 [大小规范](../c-runtime-library/size-specification.md)   
 [\_set\_output\_format](../c-runtime-library/set-output-format.md)