---
title: "使用一般文本映射 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_UNICODE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_MBCS 数据类型"
  - "_T 类型"
  - "_TCHAR 类型"
  - "_TEXT 类型"
  - "_TINT 类型"
  - "_TSCHAR 类型"
  - "_TUCHAR 类型"
  - "_TXCHAR 类型"
  - "_UNICODE 常量"
  - "一般文本数据类型"
  - "一般文本映射"
  - "映射, 一般文本"
  - "MBCS 数据类型"
  - "T 类型"
  - "TCHAR 类型"
  - "TCHAR.H 数据类型, 映射定义于"
  - "TEXT 类型"
  - "TINT 类型"
  - "TSCHAR 类型"
  - "TUCHAR 类型"
  - "TXCHAR 类型"
  - "UNICODE 常量"
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用一般文本映射
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 为简化代码的传输，便于在国际上使用， 运行库为许多数据类型、例程和其他对象提供特有的一般文本映射。  这些映射在TCHAR.H 定义。  可以使用这些名称映射编写可以为任何这三种字符集编译的泛型代码：ASCII \(SBCS\) 使用 `#define` 语句，那么，MBCS 或 Unicode，根据清单常数您定义。  一般文本映射是Microsoft扩展与ANSI不兼容的。  
  
### 一般文本映射的预处理器指令  
  
|\#define|编译版本|示例|  
|--------------|----------|--------|  
|`_UNICODE`|Unicode（宽字符）|`_tcsrev` 映射到 `_wcsrev`|  
|`_MBCS`|多字节字符|`_tcsrev` 映射到 `_mbsrev`|  
|无（默认值既未定义`_UNICODE` 也未定义 `_MBCS`）|SBCS \(ASCII\)|`_tcsrev` 映射到 `strrev`|  
  
 例如，如果在程序中定义了 `MBCS`，则TCHAR.H 中定义的一般文本函数 `_tcsrev` 映射到 `mbsrev`。或者，如果定义了 `_UNICODE` ，则映射到 `_wcsrev` 。  否则`_tcsrev`  映射到 `strrev`。  
  
 一般文本数据类型 `_TCHAR`，还定义在 TCHAR.H，映射到 `char`，则 `_MBCS` 定义，键入 `wchar_t`，则 `_UNICODE` 定义了类型 `char`，则对两个常数进行定义。  在 TCHAR.H 中还提供了其他数据类型映射以方便编程，但 `_TCHAR` 是最有用的。  
  
### 一般文本数据类型映射  
  
|一般文本数据类型名|SBCS \(\_UNICODE, \_MBCS 未定义\)|已定义 \_MBCS|已定义 \_UNICODE|  
|---------------|------------------------------------|----------------|-------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` 或 `_TEXT`|无效（由预处理器移除）|无效（由预处理器移除）|`L`（将后面的字符或字符串转换成相应的 Unicode 形式）|  
  
 对于一般文本例程映射的完整列表，变量和其他对象，请参见 [一般文本映射](../c-runtime-library/generic-text-mappings.md)。  
  
 下列代码片段阐释了用于映射到 MBCS、 Unicode和 SBCS 模型的 `_TCHAR` 和 `_tcsrev` 的用法。  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 如果已定义 `MBCS`，则预处理器映射之前片段为以下代码：  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 如果已定义 `_UNICODE`，则预处理器映射之前片段为以下代码：  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 如果既未定义 `_MBCS` 也未定义 `_UNICODE`，则预处理器将此片段映射到ASCII单字节，如下所示：  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 因此，您可以编写，维护和编译与三种字符集中任何一种的特定例程一起运行的单个源代码文件。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [一般文本映射](../c-runtime-library/generic-text-mappings.md)   
 [数据类型映射](../c-runtime-library/data-type-mappings.md)   
 [常量和全局变量映射](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [例程映射](../c-runtime-library/routine-mappings.md)   
 [简单一般文本项目](../c-runtime-library/a-sample-generic-text-program.md)