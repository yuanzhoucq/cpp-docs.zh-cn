---
title: "_rmdir、_wrmdir | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wrmdir
- _rmdir
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
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
dev_langs:
- C++
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
caps.latest.revision: 11
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 04b563468b9bc79ccd92d608dfeb4e7a3b85120a
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="rmdir-wrmdir"></a>_rmdir、_wrmdir
删除目录。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int _rmdir(  
   const char *dirname   
);  
int _wrmdir(  
   const wchar_t *dirname   
);  
```  
  
#### <a name="parameters"></a>参数  
 `dirname`  
 要删除的目录路径。  
  
## <a name="return-value"></a>返回值  
 如果成功删除目录，则这些函数将返回 0。 返回值-1 指示错误和`errno`设置为以下值之一︰  
  
 **ENOTEMPTY**  
 给定路径不是目录、路径不为空，或目录为当前工作目录或根目录。  
  
 `ENOENT`  
 路径无效。  
  
 **EACCES**  
 程序有一个打开的目录句柄。  
  
 有关这些代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_rmdir` 函数删除由 `dirname` 指定的目录。 该目录必须为空，且不能为当前工作目录或根目录。  
  
 `_wrmdir` 是 `_rmdir` 的宽字符版本；`dirname` 的 `_wrmdir` 参数是宽字符字符串。 除此以外，`_wrmdir` 和 `_rmdir` 的行为完全相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_trmdir`|`_rmdir`|`_rmdir`|`_wrmdir`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_rmdir`|\<direct.h>|  
|`_wrmdir`|\<direct.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
 请参阅 [_mkdir](../../c-runtime-library/reference/mkdir-wmkdir.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [_chdir、_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)
