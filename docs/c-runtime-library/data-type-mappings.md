---
title: "数据类型映射 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_TXCHAR"
  - "_TUCHAR"
  - "_TINT"
  - "_TSCHAR"
  - "_TCHAR"
  - "TCHAR::H"
  - "TCHAR"
  - "_T"
  - "_TEXT"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_T 类型"
  - "_TCHAR 类型"
  - "_TEXT 类型"
  - "_TINT 类型"
  - "_TSCHAR 类型"
  - "_TUCHAR 类型"
  - "_TXCHAR 类型"
  - "一般文本数据类型"
  - "T 类型"
  - "TCHAR 类型"
  - "TCHAR.H 数据类型, 映射定义于"
  - "TEXT 类型"
  - "TINT 类型"
  - "TSCHAR 类型"
  - "TUCHAR 类型"
  - "TXCHAR 类型"
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 数据类型映射
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在TCHAR.H 中定义的这些数据类型映射并依赖于程序中定义的常数 `_UNICODE` 或 `_MBCS`。  
  
 有关相关信息，请参见 [使用 \_MBCS 代码的TCHAR.H数据类型](../text/using-tchar-h-data-types-with-mbcs-code.md)。  
  
### 一般文本数据类型映射  
  
|一般文本<br /><br /> 数据类型名称|SBCS \(\_UNICODE,<br /><br /> \_MBCS not<br /><br /> 已定义\)|\_MBCS<br /><br /> 定义为|\_UNICODE<br /><br /> 定义为|  
|---------------------|------------------------------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|  
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|  
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` 或 `_TEXT`|无效（由预处理器移除）|无效（由预处理器移除）|`L`（将后面的字符或字符串转换成相应的 Unicode 形式）|  
  
## 请参阅  
 [一般文本映射](../c-runtime-library/generic-text-mappings.md)   
 [常量和全局变量映射](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [例程映射](../c-runtime-library/routine-mappings.md)   
 [简单一般文本项目](../c-runtime-library/a-sample-generic-text-program.md)   
 [使用一般文本映射](../c-runtime-library/using-generic-text-mappings.md)