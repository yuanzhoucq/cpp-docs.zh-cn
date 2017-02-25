---
title: "_splitpath、_wsplitpath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsplitpath"
  - "_splitpath"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wsplitpath"
  - "_splitpath"
  - "splitpath"
  - "_wsplitpath"
  - "_tsplitpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_splitpath 函数"
  - "_tsplitpath 函数"
  - "_wsplitpath 函数"
  - "路径名"
  - "路径名"
  - "splitpath 函数"
  - "tsplitpath 函数"
  - "wsplitpath 函数"
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _splitpath、_wsplitpath
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将路径名称分解成组件。  提供这些函数的更多安全版本；请参见 [\_splitpath\_s、\_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)。  
  
## 语法  
  
```  
void _splitpath(  
   const char *path,  
   char *drive,  
   char *dir,  
   char *fname,  
   char *ext   
);  
void _wsplitpath(  
   const wchar_t *path,  
   wchar_t *drive,  
   wchar_t *dir,  
   wchar_t *fname,  
   wchar_t *ext   
);  
```  
  
#### 参数  
 `path`  
 完整路径。  
  
 `drive`  
 驱动器号，后面加上冒号 \(`:`\)。  如果不需要使用驱动器号，可以传递此参数的 `NULL`。  
  
 `dir`  
 目录路径，包括尾部斜杠。  正斜杠 \(`/`\)，反斜杠\( `\` \)，或两者皆可。  如果不需要目录路径，可以传递此参数的 `NULL`。  
  
 `fname`  
 基文件名 \(不扩展\)。  如果不需要使用文件名，可以传递此参数的 `NULL`。  
  
 `ext`  
 文件名扩展，包括前导句点 \(`.`\)。  如果不需要使用文件名扩展，可以传递此参数的 `NULL`。  
  
## 备注  
 `_splitpath` 函数将路径分解成四个部分。  `_splitpath`它们自动处理合适的多字节字符串参数，根据当前使用的多字节代码页识别多字节字符序列.  `_wsplitpath` 是 `_splitpath` 的宽字符版本；`_wsplitpath` 的参数是宽字符串。  否则这些函数具有相同行为。  
  
 **安全性说明"** 这些函数可能会导致由缓冲区溢出问题引起的潜在威胁。  缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  这些函数更安全版本可用；参见 [\_splitpath\_s，\_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的\_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tsplitpath`|`_splitpath`|`_splitpath`|`_wsplitpath`|  
  
 完整路径的每个组件存储在单独的缓冲区中；清单常数 `_MAX_DRIVE`、`_MAX_DIR`、`_MAX_FNAME`和 `_MAX_EXT`（定义在 STDLIB.H） 指定每个文件组件的最大大小。  大于对应的清单常数的文件组件造成堆损坏。  
  
 每个缓冲区的大小必须与其对应的清单常数一样，以避免潜在的缓冲区溢出。  
  
 下表列出了清单常数的值。  
  
|名称|值|  
|--------|-------|  
|\_MAX\_DRIVE|3|  
|\_MAX\_DIR|256|  
|\_MAX\_FNAME|256|  
|\_MAX\_EXT|256|  
  
 如果没有完整路径不包含组件 \(例如，文件名\), `_splitpath` 将空字符串分配给对应的缓冲区。  
  
 您可以将 `NULL` 传递给该参数的所有 `_splitpath`，除不需要的 `path` 外。  
  
 如果 `path` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_splitpath`|\<stdlib.h\>|  
|`_wsplitpath`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见 [\_makepath](../../c-runtime-library/reference/makepath-wmakepath.md)的示例 。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_makepath、\_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [\_splitpath\_s、\_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)