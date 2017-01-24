---
title: "标志指令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "c.flags"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "标志指令 printf 函数"
  - "printf 函数的格式规范字段"
  - "打印标志指令"
  - "printf 函数, 格式规范字段"
ms.assetid: b00cbdc9-1e5c-4b30-9f56-c1ef8d383767
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 标志指令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在格式规范，第可选字段为 `flags`。  标志是指令指定输出符号、null、前导零、小数点和八进制和十六进制前缀论证和输出的字符。  多个标志可以出现在格式规范，并且标记可能会以任何排序出现。  
  
### 标记字符  
  
|Flag|含义|默认|  
|----------|--------|--------|  
|`–`|左对齐特定字段宽度的结果。|右对齐|  
|`+`|使用一个符号 \(\+ 或 \-\) 将输出值添加前缀，如果为符号类型。|符号已签名的负值仅显示值 \(\-\)。|  
|`0`|如果 `width` 由 `0`前缀，前导零添加，直到最小宽度为止。  如果 `0` 和 `–`，将忽略 `0`。  如果 `0` 指定为整数格式 \(`i`、`u`、`x`、`X`、`o`，`d`\)，而精度规范也是当前为示例中，`%04.d`\(忽略 `0`。|不填充。|  
|blank \(' '\)|如果 XML 被签名和正值，请使用空重命名输出值添加前缀。  如果两空和 \+ 标记显示，Null 被忽略。|Null 不会出现。|  
|`#`|在使用的是 `o`、`x`或 `X` 格式时，使用 `#` 标志 0x、0X，0，分别重命名所有非零值输出前缀。|Null 不会出现。|  
||当使用了具有 `e`、`E`、`f`、`a` 或 `A` 格式时，`#` 标志来强制输出值包含小数点。|当数字其后，小数点显示。|  
||当使用了与 `g` 或 `G` 格式时，`#` 标志来强制移除包含小数点的输出值并防止尾随零的截断。<br /><br /> 将忽略对 `c`、`d`、`i`、`u`或 `s`。|当数字其后，小数点显示。  截断尾部零。|  
  
## 请参阅  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式规范语法：printf 和 wprintf 函数](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [printf 宽度规范](../c-runtime-library/printf-width-specification.md)   
 [精度规范](../c-runtime-library/precision-specification.md)   
 [大小规范](../c-runtime-library/size-specification.md)   
 [printf 类型字段字符](../c-runtime-library/printf-type-field-characters.md)