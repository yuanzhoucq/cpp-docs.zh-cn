---
title: "_putenv、_wputenv | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
dev_langs:
- C++
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: d91f7b780c8f17fbe1e12a195b6a7cf2eaad3d2f
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="putenv-wputenv"></a>_putenv、_wputenv
创建、修改或删除环境变量。 提供这些函数的更多安全版本；请参阅 [_putenv_s、_wputenv_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _putenv(  
   const char *envstring   
);  
int _wputenv(  
   const wchar_t *envstring   
);  
```  
  
#### <a name="parameters"></a>参数  
 `envstring`  
 环境字符串定义。  
  
## <a name="return-value"></a>返回值  
 返回成功时为 0 或-1，如果出现错误。  
  
## <a name="remarks"></a>备注  
 `_putenv` 函数添加了新的环境变量，或修改了现有环境变量的值。 环境变量定义过程执行的环境（例如待与程序链接的库的默认搜索路径）。 `_wputenv` 是 `_putenv` 的宽字符版本；`envstring` 的 `_wputenv` 参数是宽字符字符串。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tputenv`|`_putenv`|`_putenv`|`_wputenv`|  
  
 `envstring` 参数必须是指向窗体 `varname=string` 的字符串的指针，其中 `varname` 是要添加或修改的环境变量的名称，而 `string` 是变量的值。 如果 `varname` 已是环境的一部分，则其值将由 `string` 替代；否则，新的 `varname` 变量及其 `string` 值将添加到环境中。 可以通过指定一个空 `string`（即仅指定 `varname=`）来从环境中移除变量。  
  
 `_putenv` 和 `_wputenv` 仅会影响本地到当前进程的环境；不能用于修改命令级别环境。 也就是说，这些函数只在可由运行时库访问的数据结构上操作，并不在操作系统为进程创建的环境段上操作。 在当前进程终止时，环境将还原到调用进程的级别（在大多数情况下，为操作系统级别）。 但是，可以将修改后的环境传递给由 `_spawn`、`_exec` 或 `system` 创建的任何新进程，这些新进程将获取由 `_putenv` 和 `_wputenv` 添加的所有新项。  
  
 不直接更改环境条目：改用 `_putenv` 或 `_wputenv` 更改它。 具体而言，直接释放 `_environ[]` 全局数组的元素可能会导致寻址无效的内存。  
  
 `getenv` 和 `_putenv` 使用全局变量 `_environ` 来访问环境表；`_wgetenv` 和 `_wputenv` 使用 `_wenviron`。 `_putenv`和`_wputenv`可能会更改的值`_environ`和`_wenviron`，因此失效`_envp`参数`main`和`_wenvp`参数`wmain`。 因此，使用 `_environ` 或 `_wenviron` 来访问的环境信息是安全的。 有关 `_putenv` 和 `_wputenv` 与全局变量关系的详细信息，请参阅 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv` 和 `_getenv` 系列的函数不是线程安全函数。 当 `_putenv` 修改字符串时，`_getenv` 可能会返回字符串指针，从而导致随机性失败。 确保对这些函数的调用同步。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_putenv`|\<stdlib.h>|  
|`_wputenv`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 有关如何使用 `_putenv` 的示例，请参阅 [getenv、_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)。  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [getenv、_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_searchenv、_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)
