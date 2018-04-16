---
title: "_splitpath_s、_wsplitpath_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wsplitpath_s
- _splitpath_s
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
dev_langs:
- C++
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9baa71ca1a3d624c08df8ff1cbd14a9386e1b83d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s、_wsplitpath_s
将路径名称分解成组件。 这些版本的 [_splitpath、_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 [in] `path`  
 完整路径。  
  
 [out] `drive`  
 后跟一个冒号 (`:`) 的驱动器号。 如果不需要驱动器号，则可为此参数传递 `NULL`。  
  
 [in] `driveNumberOfElements`  
 `drive` 缓冲区大小（以单字节字符或宽字符为单位）。 如果 `drive` 是 `NULL`，则该值必须为 0。  
  
 [out] `dir`  
 目录路径，包括尾部反斜杠。 正斜杠 ( `/` )、反斜杠 ( `\` )，或两者均使用。 如果不需要目录路径，则可为此参数传递 `NULL`。  
  
 [in] `dirNumberOfElements`  
 `dir` 缓冲区大小（以单字节字符或宽字符为单位）。 如果 `dir` 是 `NULL`，则该值必须为 0。  
  
 [out] `fname`  
 基文件名（不带扩展名）。 如果不需要文件名，则可为此参数传递 `NULL`。  
  
 [in] `nameNumberOfElements`  
 `fname` 缓冲区大小（以单字节字符或宽字符为单位）。 如果 `fname` 是 `NULL`，则该值必须为 0。  
  
 [out] `ext`  
 文件扩展名，包括前导句点 (**.**)。如果不需要文件扩展名，则可为此参数传递 `NULL`。  
  
 [in] `extNumberOfElements`  
 `ext` 缓冲区大小（以单字节字符或宽字符为单位）。 如果 `ext` 是 `NULL`，则该值必须为 0。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
### <a name="error-conditions"></a>错误条件  
  
|条件|返回值|  
|---------------|------------------|  
|`path` 为 `NULL`|`EINVAL`|  
|`drive` 是 `NULL`，则 `driveNumberOfElements` 为非零|`EINVAL`|  
|`drive` 是非 `NULL`，则 `driveNumberOfElements` 为零|`EINVAL`|  
|`dir` 是 `NULL`，则 `dirNumberOfElements` 为非零|`EINVAL`|  
|`dir` 是非 `NULL`，则 `dirNumberOfElements` 为零|`EINVAL`|  
|`fname` 是 `NULL`，则 `nameNumberOfElements` 为非零|`EINVAL`|  
|`fname` 是非 `NULL`，则 `nameNumberOfElements` 为零|`EINVAL`|  
|`ext` 是 `NULL`，则 `extNumberOfElements` 为非零|`EINVAL`|  
|`ext` 是非 `NULL`，则 `extNumberOfElements` 为零|`EINVAL`|  
  
 如果发生上述情况之一，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
 如果所有缓冲区均过短而无法保存结果，这些函数会将所有缓冲区清除为空字符串，并将 `errno` 设置为 `ERANGE`，返回 `ERANGE`。  
  
## <a name="remarks"></a>备注  
 `_splitpath_s` 函数将路径分解成其的四个组件。 `_splitpath_s` 将根据情况自动处理多字节字符串参数，根据当前正在使用的多字节代码页识别多字节字符序列。 `_wsplitpath_s` 是 `_splitpath_s` 的宽字符版本；`_wsplitpath_s` 的参数是宽字符串。 否则这些函数具有相同行为  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsplitpath_s`|`_splitpath_s`|`_splitpath_s`|`_wsplitpath_s`|  
  
 完整路径的每个组件均存储在单独的缓冲区中；清单常量 `_MAX_DRIVE`、`_MAX_DIR`、`_MAX_FNAME` 和 `_MAX_EXT`（在 STDLIB.H 中定义）指定每个文件组件的最大可允许大小。 文件组件大于相应清单常量会导致堆损坏。  
  
 下表列出了清单常量的值。  
  
|名称|值|  
|----------|-----------|  
|_MAX_DRIVE|3|  
|_MAX_DIR|256|  
|_MAX_FNAME|256|  
|_MAX_EXT|256|  
  
 如果完整路径不包含组件（例如，文件名），则 `_splitpath_s` 会将空字符串分配给相应的缓冲区。  
  
 在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_splitpath_s`|\<stdlib.h>|  
|`_wsplitpath_s`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 请参阅 [_makepath_s、_wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_splitpath、_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)