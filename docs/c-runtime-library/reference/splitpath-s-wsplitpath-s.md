---
title: "_splitpath_s、_wsplitpath_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsplitpath_s"
  - "_splitpath_s"
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
  - "_wsplitpath_s"
  - "splitpath_s"
  - "_splitpath_s"
  - "wsplitpath_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_splitpath_s 函数"
  - "_wsplitpath_s 函数"
  - "路径名"
  - "路径名"
  - "splitpath_s 函数"
  - "wsplitpath_s 函数"
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _splitpath_s、_wsplitpath_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Breaks a path name into components.  These are versions of [\_splitpath, \_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md) with security enhancements as described in [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md).  
  
## 语法  
  
```  
errno_t _splitpath_s(  
   const char * path,  
   char * drive,  
   size_t driveNumberOfElements,  
   char * dir,  
   size_t dirNumberOfElements,  
   char * fname,  
   size_t nameNumberOfElements,  
   char * ext,   
   size_t extNumberOfElements  
);  
errno_t _wsplitpath_s(  
   const wchar_t * path,  
   wchar_t * drive,  
   size_t driveNumberOfElements,  
   wchar_t *dir,  
   size_t dirNumberOfElements,  
   wchar_t * fname,  
   size_t nameNumberOfElements,  
   wchar_t * ext,  
   size_t extNumberOfElements  
);  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _splitpath_s(  
   const char *path,  
   char (&drive)[drivesize],  
   char (&dir)[dirsize],  
   char (&fname)[fnamesize],  
   char (&ext)[extsize]  
); // C++ only  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _wsplitpath_s(  
   const wchar_t *path,  
   wchar_t (&drive)[drivesize],  
   wchar_t (&dir)[dirsize],  
   wchar_t (&fname)[fnamesize],  
   wchar_t (&ext)[extsize]  
); // C++ only  
```  
  
#### 参数  
 \[in\] `path`  
 Full path.  
  
 \[out\] `drive`  
 Drive letter, followed by a colon \(`:`\).  You can pass `NULL` for this parameter if you do not need the drive letter.  
  
 \[in\] `driveNumberOfElements`  
 The size of the `drive` buffer in single\-byte or wide characters.  如果`drive`是`NULL`，该值必须是0。  
  
 \[out\] `dir`  
 目录路径，包括尾部斜杠。  正斜杠 \(`/` \),反斜杠\( `\` \)，或两者皆可。  如果不需要目录路径，可以传递此参数的 `NULL`。  
  
 \[in\] `dirNumberOfElements`  
 单字节字符或宽字符的`dir`缓冲区的大小。  如果`dir`是`NULL`，该值必须是0。  
  
 \[out\] `fname`  
 基文件名 \(不带扩展名\)。  如果不需要使用文件名，可以传递此参数的 `NULL`。  
  
 \[in\] `nameNumberOfElements`  
 单字节字符或宽字符的`fname`缓冲区的大小。  如果`fname`是`NULL`，该值必须是0。  
  
 \[out\] `ext`  
 文件名扩展，包括的前导句点 \(**.**\)。如果不需要文件扩展名，则可以传递此参数的 `NULL`。  
  
 \[in\] `extNumberOfElements`  
 单字节字符或宽字符的`ext`缓冲区的大小。  如果`ext`是`NULL`，该值必须是0。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
### 错误情况  
  
|条件|返回值|  
|--------|---------|  
|`path` 为  `NULL`|`EINVAL`|  
|`drive` 为 `NULL`，则 `driveNumberOfElements` 为非零|`EINVAL`|  
|`drive` 为非 `NULL`，则 `driveNumberOfElements` 为零|`EINVAL`|  
|`dir` 为 `NULL`，则 `dirNumberOfElements` 为非零|`EINVAL`|  
|`dir` 为非 `NULL`，则 `dirNumberOfElements` 为零|`EINVAL`|  
|`fname` 为 `NULL`，则 `nameNumberOfElements` 为非零|`EINVAL`|  
|`fname` 为非 `NULL`，则 `nameNumberOfElements` 为零|`EINVAL`|  
|`ext` 为 `NULL`，则 `extNumberOfElements` 为非零|`EINVAL`|  
|`ext` 为非 `NULL`，则 `extNumberOfElements` 为零|`EINVAL`|  
  
 如果任何以上状态发生，调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回`EINVAL`。  
  
 如果任何缓冲区太短而无法存储结果，则这些函数清除所有缓冲区为空字符串，将 `errno` 设置为 `ERANGE`,并返回 `ERANGE`。  
  
## 备注  
 `_splitpath_s` 函数将路径分解成四个部分。  `_splitpath_s` 它们自动处理合适的多字节字符串参数，根据当前使用的多字节代码页识别多字节字符序列.  `_wsplitpath_s`  是 `_splitpath_s` 的宽字符版本；`_``wsplitpath_s` ``  的参数是宽字符串。  否则这些函数具有相同行为。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE& 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tsplitpath_s`|`_splitpath_s`|`_splitpath_s`|`_wsplitpath_s`|  
  
 完整路径的每个组件存储在单独的缓冲区中；清单常数 `_MAX_DRIVE`、`_MAX_DIR`、`_MAX_FNAME`和 `_MAX_EXT` \(定义在 STDLIB.H\) 指定每个文件组件的最大允许大小。  大于对应的清单常数的文件组件造成堆损坏。  
  
 下表列出了清单常数的值。  
  
|名称|值|  
|--------|-------|  
|\_MAX\_DRIVE|3|  
|\_MAX\_DIR|256|  
|\_MAX\_FNAME|256|  
|\_MAX\_EXT|256|  
  
 如果没有完整路径不包含组件 \(例如，文件名\), `_splitpath_s` 将空字符串分配给对应的缓冲区。  
  
 在 C\+\+ 中，使用这些函数是由重载模板简化；该重载可以自动推断缓冲区长度，而无需指定范围参数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_splitpath_s`|\<stdlib.h\>|  
|`_wsplitpath_s`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见 [\_makepath\_s、\_wmakepath\_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)中的示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_splitpath、\_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_makepath、\_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)