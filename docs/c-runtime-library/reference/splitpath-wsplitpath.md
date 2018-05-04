---
title: _splitpath、_wsplitpath | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wsplitpath
- _splitpath
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
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
dev_langs:
- C++
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 220e2befc40dba342a7f8c2aa4c94294bc667ce0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="splitpath-wsplitpath"></a>_splitpath、_wsplitpath

将路径名称分解成组件。 提供这些函数的更多安全版本；请参阅 [_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*路径*完整路径。

*驱动器*驱动器号后跟一个冒号 (**:**)。 你可以将传递**NULL**为此参数，如果你不需要的驱动器号。

*dir*目录路径，包括尾部反斜杠。 正斜杠 ( **/** )，反斜杠 ( **\\** )，或者可能使用两者。 你可以将传递**NULL**为此参数，如果你不需要的目录路径。

*fname*基文件名 （无扩展名）。 你可以将传递**NULL**为此参数，如果你不需要文件名。

*ext*文件名扩展，包括前导段 (**。**)。 你可以将传递**NULL**为此参数，如果你不需要文件扩展名。

## <a name="remarks"></a>备注

**_Splitpath**函数将路径分成其四个组件。 **_splitpath**自动处理多字节字符字符串自变量，根据需要，根据当前正在使用的多字节代码页识别多字节字符序列。 **_wsplitpath**是宽字符版本的 **_splitpath**; 的自变量 **_wsplitpath**是宽字符字符串。 否则这些函数具有相同行为。

**安全说明**这些函数会引发由缓冲区溢出问题带来的潜在威胁。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。 提供这些函数的更多安全版本；请参阅 [_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

每个组件的完整路径存储在单独的缓冲区;清单常量 **_MAX_DRIVE**， **_MAX_DIR**， **_MAX_FNAME**，和 **_MAX_EXT** （在 STDLIB 中定义。H） 指定每个文件组件的最大大小。 文件组件大于相应清单常量会导致堆损坏。

每个缓冲区必须与其相应的清单常量一样大，以避免潜在的缓冲区溢出。

下表列出了清单常量的值。

|名称|值|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

如果完整路径不包含组件 （例如，文件名）， **_splitpath**分配为空字符串转换为对应的缓冲区。

你可以将传递**NULL**到 **_splitpath**以外的其他任何参数*路径*不需要。

如果*路径*是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**和该函数将返回**EINVAL**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_makepath](makepath-wmakepath.md) 的示例。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
