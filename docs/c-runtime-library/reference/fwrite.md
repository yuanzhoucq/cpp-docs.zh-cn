---
title: "fwrite | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fwrite"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fwrite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fwrite 函数"
  - "流, 将数据写入到"
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# fwrite
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将数据写入流。  
  
## 语法  
  
```  
size_t fwrite(    const void *buffer,    size_t size,    size_t count,    FILE *stream  );  
```  
  
#### 参数  
 `buffer`  
 指向要写入的数据的指针。  
  
 `size`  
 项大小（以字节为单位）。  
  
 `count`  
 要写入的项的最大数量。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 `fwrite` 返回实际写入的整个项的数量，如果发生错误，则该数量可能会小于 `count`。  此外，如果发生错误，则无法确定文件位置指示器。  如果 `stream` 或 `buffer` 是空指针，或者如果在 Unicode 模式下指定了要写入的奇数个字节，则该函数将调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 0。  
  
## 备注  
 `fwrite` 函数最多将 `count` 个项从 `buffer` 写入到输出 `stream`，每个项的长度为 `size`。  与 `stream` 相关联的文件指针（如果存在）以实际写入的字节数为增量进行递增。  如果在文本模式下打开 `stream`，则会将每个换行符替换为回车符 – 换行符对。  该替换不会影响返回值。  
  
 当在 Unicode 转换模式下打开 `stream` 时（例如，通过调用 `fopen` 并使用包含 `ccs=UNICODE`、`ccs=UTF-16LE` 或 `ccs=UTF-8` 的模式参数打开 `stream` 时，或者通过使用 `_setmode` 和包含 `_O_WTEXT`、`_O_U16TEXT` 或 `_O_U8TEXT` 的模式参数将该模式更改为 Unicode 转换模式时），会将 `buffer` 解释为指向包含 UTF\-16 数据的 `wchar_t` 数组的指针。  尝试在此模式下写入奇数个字节会导致参数验证错误。  
  
 因为此函数会锁定调用线程，因此它是线程安全的。  有关非锁定版本，请参阅 `_fwrite_nolock`。  
  
## 要求  
  
|函数|必需的标头|  
|--------|-----------|  
|`fwrite`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [fread](../../c-runtime-library/reference/fread.md) 示例。  
  
## .NET Framework 等效项  
 [System::IO::FileStream::Write](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [\_fwrite\_nolock](../../c-runtime-library/reference/fwrite-nolock.md)   
 [\_write](../../c-runtime-library/reference/write.md)