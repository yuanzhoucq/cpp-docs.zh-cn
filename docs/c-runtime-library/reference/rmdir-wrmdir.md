---
title: _rmdir、_wrmdir
ms.date: 11/04/2016
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
ms.openlocfilehash: 0d0d9a25b70746174a66abbe088b297a5d9a0942
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327989"
---
# <a name="rmdir-wrmdir"></a>_rmdir、_wrmdir

删除目录。

## <a name="syntax"></a>语法

```C
int _rmdir(
   const char *dirname
);
int _wrmdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>参数

*dirname*<br/>
要删除的目录路径。

## <a name="return-value"></a>返回值

如果成功删除目录，则这些函数将返回 0。 返回值-1 指示错误和**errno**设置为以下值之一：

|errno 值|条件|
|-|-|
| **ENOTEMPTY** | 给定路径不是目录、路径不为空，或目录为当前工作目录或根目录。 |
| **ENOENT** | 路径无效。 |
| **EACCES** | 程序有一个打开的目录句柄。 |

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Rmdir**函数将删除指定的目录*dirname*。 该目录必须为空，且不能为当前工作目录或根目录。

**_wrmdir**是宽字符版本 **_rmdir**; *dirname*参数 **_wrmdir**是宽字符字符串。 **_wrmdir**并 **_rmdir**行为相同。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<direct.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

请参阅 [_mkdir](mkdir-wmkdir.md) 的示例。

## <a name="see-also"></a>请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
