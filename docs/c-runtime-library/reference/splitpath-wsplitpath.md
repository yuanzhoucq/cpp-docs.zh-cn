---
title: _splitpath、_wsplitpath
ms.date: 4/2/2020
api_name:
- _wsplitpath
- _splitpath
- _o__splitpath
- _o__wsplitpath
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
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
ms.openlocfilehash: 6798f93b2d1bc18a190b3b015bf8c882a3fa8a37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355614"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath、_wsplitpath

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

*路径*<br/>
完整路径。

*驱动*<br/>
驱动器号，后跟冒号 （**。** 如果不需要驱动器号，可以传递此参数的**NULL。**

*dir*<br/>
目录路径，包括尾部反斜杠。 可使用向前斜**/** 杠 （）、斜**\\**杠 （） 或两者。 如果不需要目录路径，可以传递此参数的**NULL。**

*fname*<br/>
基文件名（无扩展名）。 如果不需要文件名，可以传递此参数的**NULL。**

*内线*<br/>
文件名扩展名，包括前导期 **（. 。** 如果不需要文件名扩展名，可以传递此参数的**NULL。**

## <a name="remarks"></a>备注

**_splitpath**函数将路径分解为四个组件。 **_splitpath**根据需要自动处理多字节字符串参数，根据当前使用的多字节代码页识别多字节字符序列。 **_wsplitpath**是 **_splitpath**的宽字符版本;要 **_wsplitpath**的参数是宽字符字符串。 否则这些函数具有相同行为。

**安全说明**这些函数会引发由缓冲区溢出问题带来的潜在威胁。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。 这些函数的更安全的版本可用;见[_splitpath_s，_wsplitpath_s。](splitpath-s-wsplitpath-s.md)

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

完整路径的每个组件都存储在单独的缓冲区中;清单常量 **_MAX_DRIVE、_MAX_DIR、_MAX_FNAME**和 **_MAX_EXT（** 在 STDLIB 中定义）。 **_MAX_DRIVE** **_MAX_FNAME**H） 指定每个文件组件的最大大小。 文件组件大于相应清单常量会导致堆损坏。

每个缓冲区必须与其相应的清单常量一样大，以避免潜在的缓冲区溢出。

下表列出了清单常量的值。

|“属性”|“值”|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

如果完整路径不包含组件（例如文件名 **），_splitpath**将空字符串分配给相应的缓冲区。

您可以将**NULL**传递给 **_splitpath**除*路径*之外不需要的任何参数。

如果*路径*为**NULL，** 则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续 **，errno**设置为**EINVAL，** 并且函数返回**EINVAL**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_makepath](makepath-wmakepath.md) 的示例。

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
