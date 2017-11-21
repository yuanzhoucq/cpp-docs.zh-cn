---
title: "_putenv_s、_wputenv_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wputenv_s
- _putenv_s
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
apitype: DLLExport
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
dev_langs: C++
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e3e23b45eb96faf88924323850550feaa1fbf34f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="putenvs-wputenvs"></a>_putenv_s、_wputenv_s
创建、修改或删除环境变量。 这些是安全性增强的 [_putenv、_wputenv](../../c-runtime-library/reference/putenv-wputenv.md) 版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/en-us/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _putenv_s(  
   const char *name,  
   const char *value   
);  
errno_t _wputenv_s(  
   const wchar_t *name,  
   const wchar_t *value  
);  
```  
  
#### <a name="parameters"></a>参数  
 `name`  
 环境变量名称。  
  
 `value`  
 要将环境变量设置为的值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0；否则，返回错误代码。  
  
### <a name="error-conditions"></a>错误条件  
  
|`name`|`value`|返回值|  
|------------|-------------|------------------|  
|`NULL`|任何|`EINVAL`|  
|任何|`NULL`|`EINVAL`|  
  
 如果发生某个错误条件，这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_putenv_s` 函数添加了新的环境变量，或修改了现有环境变量的值。 环境变量定义过程执行的环境（例如待与程序链接的库的默认搜索路径）。 `_wputenv_s` 是 `_putenv_s` 的宽字符版本；`envstring` 的 `_wputenv_s` 参数是宽字符字符串。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tputenv_s`|`_putenv_s`|`_putenv_s`|`_wputenv_s`|  
  
 `name` 是要添加或修改的环境变量的名称，`value` 是变量的值。 如果 `name` 已是环境的一部分，则其值将由 `value` 替代；否则，新的 `name` 变量及其 `value` 值将添加到环境中。 您可以通过为 `value` 指定空字符串（即 ""）来从环境中移除变量。  
  
 `_putenv_s` 和 `_wputenv_s` 仅会影响本地到当前进程的环境；不能用于修改命令级别环境。 这些函数仅对运行库可访问的数据结构执行，而不对操作系统为进程创建的环境“段”运行。 在当前进程终止时，环境将还原到调用进程的级别，它在大多数情况下为操作系统级别。 但是，可以将修改后的环境传递给由 `_spawn`、`_exec` 或 `system` 创建的任何新进程，这些新进程将获取由 `_putenv_s` 和 `_wputenv_s` 添加的所有新项。  
  
 不直接更改环境条目；而是使用 `_putenv_s` 或 `_wputenv_s` 更改它。 具体而言，直接释放 `_environ[]` 全局数组的元素可能会导致对无效内存寻址。  
  
 `getenv` 和 `_putenv_s` 使用全局变量 `_environ` 来访问环境表；`_wgetenv` 和 `_wputenv_s` 使用 `_wenviron`。 `_putenv_s` 和 `_wputenv_s` 可能更改 `_environ` 和 `_wenviron` 的值，因此会使 `envp` 的 `main` 参数和 `_wenvp` 的 `wmain` 参数无效。 因此，使用 `_environ` 或 `_wenviron` 来访问的环境信息是安全的。 有关 `_putenv_s` 和 `_wputenv_s` 与全局变量关系的详细信息，请参阅 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv_s` 和 `_getenv_s` 系列的函数不是线程安全函数。 当 `_getenv_s` 修改字符串时，`_putenv_s` 会返回字符串指针，从而导致随机失败。 确保对这些函数的调用同步。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_putenv_s`|\<stdlib.h>|  
|`_wputenv_s`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 有关说明如何使用 `_putenv_s` 的示例，请参阅 [getenv_s、_wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)。  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [getenv、_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_searchenv、_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)