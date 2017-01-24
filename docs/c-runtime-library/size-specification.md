---
title: "大小规范 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "size"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "printf 函数, 格式规范字段"
ms.assetid: 525dc5d8-e70a-4797-a6a0-ec504a27355c
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 大小规范
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在格式规范中，第四个字段是转换说明符的参数长度修饰符。  `size` 字段作为 `type` 字段的前缀 — `h`、`l`、`w`、`I`、`I32`、`I64` 和 `ll` — 指定对应参数的“大小”（长型或短型、32 位或 64 位、单字节字符或宽字符）具体取决于它们修饰的转换说明符。  这些大小前缀在 `printf` 和 `wprintf` 系列函数中与 `type` 字符一起使用，来指定参数长度的解释（如下表中所示）。  `size` 字段对于某些参数类型是可选的。  未指定任何大小前缀时，格式化程序使用整数参数（例如，带符号或无符号 `char`、`short`、`int`、`long` 和枚举类型）作为 32 位 `int` 类型，而使用浮点参数作为 64 位 `double` 类型。  这与变量参数列表的默认参数提升规则相匹配。  有关参数提升的详细信息，请参阅[省略号和默认自变量](../misc/ellipses-and-default-arguments.md)。  在 32 位和 64 位系统上，64 位整数参数的格式规范必须包含大小前缀 `ll` 或 `I64`。  否则，格式化程序的行为是不明确的。  
  
 某些类型在 32 位和 64 位代码中具有不同大小。  例如，`size_t` 在针对 x86 编译的代码中是 32 位长，而在针对 x64 编译的代码中是 64 位。  若要为可变宽度类型创建与平台无关的格式设置代码，可以使用可变宽度参数长度修饰符。  或者，使用 64 位参数长度修饰符，并将可变宽度参数类型显式提升为 64 位。  特定于 Microsoft 的 `I` 参数长度修饰符可处理可变宽度整数参数。  
  
> [!NOTE]
>  `I`、`I32` 和 `I64` 长度修饰符前缀是 Microsoft 扩展，与 ANSI 不兼容。  `h` 前缀（在用于 `char` 类型的数据时）、`w` 前缀（在用于 `wchar_t` 类型的数据时）和 `l` 前缀（在用于 `double` 类型的数据时）是 Microsoft 扩展。  不支持 `hh`、`j`、`z` 和 `t` 长度前缀。  
  
### printf 和 wprintf 格式类型说明符的大小前缀  
  
|若要指定|使用前缀|及类型说明符|  
|----------|----------|------------|  
|`long int`|`l`（小写 L）|`d`、`i`、`o`、`x` 或 `X`|  
|`long unsigned int`|`l`|`o`、`u`、`x` 或 `X`|  
|`long long`|`ll`|`d`、`i`、`o`、`x` 或 `X`|  
|`short int`|`h`|`d`、`i`、`o`、`x` 或 `X`|  
|`short unsigned int`|`h`|`o`、`u`、`x` 或 `X`|  
|`__int32`|`I32`|`d`、`i`、`o`、`x` 或 `X`|  
|`unsigned __int32`|`I32`|`o`、`u`、`x` 或 `X`|  
|`__int64`|`I64`|`d`、`i`、`o`、`x` 或 `X`|  
|`unsigned __int64`|`I64`|`o`、`u`、`x` 或 `X`|  
|`ptrdiff_t`（即，在 32 位平台上是 `__int32`，在 64 位平台上是 `__int64`）|`I`|`d`、`i`、`o`、`x` 或 `X`|  
|`size_t`（即，在 32 位平台上是 `unsigned __int32`，在 64 位平台上是 `unsigned __int64`）|`I`|`o`、`u`、`x` 或 `X`|  
|`long double`（在 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 中，虽然 `long double` 是不同的类型，但是它具有与 `double` 相同的内部表示形式。）|`l` 或 `L`|`a`、`A`、`e`、`E`、`f`、`g` 或 `G`。|  
|单字节字符与 `printf` 和 `wprintf` 函数。  （`hc` 或 `hC` 类型说明符与 `printf` 函数中的 `c` 以及 `wprintf` 函数中的 `C` 是同义的。）|`h`|`c` 或 `C`|  
|宽字符与 `printf` 和 `wprintf` 函数。  （`lc`、`lC`、`wc` 或 `wC` 类型说明符与 `printf` 函数中的 `C` 以及 `wprintf` 函数中的 `c` 是同义的。）|`l` 或 `w`|`c` 或 `C`|  
|单字节字符串与 `printf` 和 `wprintf` 函数。  （`hs` 或 `hS` 类型说明符与 `printf` 函数中的 `s` 以及 `wprintf` 函数中的 `S` 是同义的。）|`h`|`s`、`S` 或 `Z`|  
|宽字符串与 `printf` 和 `wprintf` 函数。  （`ls`、`lS`、`ws` 或 `wS` 类型说明符与 `printf` 函数中的 `S` 以及 `wprintf` 函数中的 `s` 是同义的。）|`l` 或 `w`|`s`、`S` 或 `Z`|  
  
## 请参阅  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式规范语法：printf 和 wprintf 函数](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [标志指令](../c-runtime-library/flag-directives.md)   
 [printf 宽度规范](../c-runtime-library/printf-width-specification.md)   
 [精度规范](../c-runtime-library/precision-specification.md)   
 [printf 类型字段字符](../c-runtime-library/printf-type-field-characters.md)