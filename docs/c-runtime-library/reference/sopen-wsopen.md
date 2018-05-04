---
title: _sopen、_wsopen | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _sopen
- _wsopen
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsopen
- wsopen
- _sopen
- _tsopen
dev_langs:
- C++
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e8d7f7624dc8c521186aa697ad8825c77e0108f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="sopen-wsopen"></a>_sopen、_wsopen

打开文件以供共享。 提供了这些函数的更安全版本： 请参阅[_sopen_s、 _wsopen_s](sopen-s-wsopen-s.md)。

## <a name="syntax"></a>语法

```C
int _sopen(
   const char *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
int _wsopen(
   const wchar_t *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
```

### <a name="parameters"></a>参数

*filename*<br/>
文件名。

*oflag*<br/>
允许的操作类型。

*shflag*<br/>
允许的共享类型。

*pmode*<br/>
权限设置。

## <a name="return-value"></a>返回值

其中每个函数都将为打开的文件返回文件描述符。

如果*filename*或*oflag*是**NULL**指针，或如果*oflag*或*shflag*不在有效范围的值的无效参数处理程序调用时中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回-1 并设置**errno**为以下值之一。

|errno 值|条件|
|-|-|
**EACCES**|给定路径是目录，或者文件是只读的，但是已尝试打开以供写入操作。
**EEXIST**|**_O_CREAT**和 **_O_EXCL**标志已指定，但*filename*已存在。
**EINVAL**|无效*oflag*或*shflag*自变量。
**EMFILE**|没有更多可用的文件描述符。
**ENOENT**|未找到文件或路径。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Sopen**函数将打开指定的文件*filename*和使文件共享的读取或写入，做好准备，由定义*oflag*和*shflag*. **_wsopen**是宽字符版本的 **_sopen**; *filename*参数 **_wsopen**是宽字符字符串。 **_wsopen**和 **_sopen**否则具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

整数表达式*oflag*通过合并一个或多个中定义的以下清单常量形成\<fcntl.h >。 当两个或多个常量构成参数*oflag*，使用按位 OR 运算符合并它们: ( **&#124;** )。

|*oflag*常量|行为|
|-|-|
**_O_APPEND**|在执行每个写入操作之前，将文件指针移动到文件末尾。
**_O_BINARY**|在二进制（未转换）模式下打开该文件。 （有关二进制模式的说明，请参阅 [fopen](fopen-wfopen.md)。）
**_O_CREAT**|创建文件并打开它以供写入。 如果指定的文件不起作用*filename*存在。 *Pmode*时，参数是必需 **_O_CREAT**指定。
**_O_CREAT** &AMP;#124; **_O_SHORT_LIVED**|创建一个文件作为临时文件，如果可能，请不要将它刷新到磁盘中。 *Pmode*时，参数是必需 **_O_CREAT**指定。
**_O_CREAT** &AMP;#124; **_O_TEMPORARY**|创建一个文件作为临时文件；在关闭最后一个文件描述符时，删除该文件。 *Pmode*时，参数是必需 **_O_CREAT**指定。
**_O_CREAT**&AMP;#124; ` _O_EXCL`|如果由指定的文件，则返回一个错误值*filename*存在。 仅当与一起使用时应用 **_O_CREAT**。
**_O_NOINHERIT**|阻止创建共享文件描述符。
**_O_RANDOM**|指定缓存针对（但不限于）从磁盘的随机访问进行优化。
**_O_RDONLY**|打开文件以供只读。 不能与指定 **_O_RDWR**或 **_O_WRONLY**。
**_O_RDWR**|打开文件以供读取和写入。 不能与指定 **_O_RDONLY**或 **_O_WRONLY**。
**_O_SEQUENTIAL**|指定缓存针对（但不限于）从磁盘的顺序访问进行优化。
**_O_TEXT**|在文本（转换）模式下打开文件。 （有关详细信息，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](fopen-wfopen.md)。）
**_O_TRUNC**|打开文件并将其长度截断为零；该文件必须具有写入权限。 不能与指定 **_O_RDONLY**。 **_O_TRUNC**用于 **_O_CREAT**打开一个现有文件或创建一个文件。 **注意：** **_O_TRUNC**标志会损坏指定文件的内容。
**_O_WRONLY**|打开文件以供只写。 不能与指定 **_O_RDONLY**或 **_O_RDWR**。
**_O_U16TEXT**|在 Unicode UTF-16 模式下打开文件。
**_O_U8TEXT**|在 Unicode UTF-8 模式下打开文件。
**_O_WTEXT**|在 Unicode 模式下打开文件。

若要指定文件访问模式，你必须指定 **_O_RDONLY**， **_O_RDWR**，或 **_O_WRONLY**。 对于访问模式，不存在默认值。

通过使用在 Unicode 模式下打开文件时 **_O_WTEXT**， **_O_U8TEXT**，或 **_O_U16TEXT**、 输入函数将从文件读取到 utf-16 数据的数据转换存储类型为**wchar_t**。 写入到在 Unicode 模式下打开的文件的函数需要包含存储为类型的 utf-16 数据的缓冲区**wchar_t**。 如果将文件编码为 UTF-8，则在写入它时，UTF-16 数据会转换为 UTF-8；在读取它时，该文件的 UTF-8 编码的内容会转换为 UTF-16。 尝试在 Unicode 模式下读取或写入奇数个字节会导致参数验证错误。 若要读取或写入在你的程序中存储为 UTF-8 的数据，请使用文本或二进制文件模式，而不是 Unicode 模式。 你应负责所有必需的编码转换。

如果 **_sopen**使用调用 **_O_WRONLY** | **_O_APPEND** （追加模式） 和 **_O_WTEXT**， **_O_U16TEXT**，或 **_O_U8TEXT**，它首先尝试打开文件进行读取和写入、 读取 BOM，然后重新打开它供只写。 如果无法打开该文件以供读取和写入，则它将打开该文件以供只写，并使用 Unicode 模式设置的默认值。

自变量*shflag*是常量表达式包含在中定义的以下清单常量之一\<share.h >。

|*shflag*常量|行为|
|-|-|
**_SH_DENYRW**|拒绝对文件的读取和写入访问。
**_SH_DENYWR**|拒绝对文件的写入访问。
**_SH_DENYRD**|拒绝对文件的读取访问。
**_SH_DENYNO**|允许读取和写入访问。

*Pmode*参数是必需的仅当 **_O_CREAT**指定。 如果文件不存在， *pmode*指定第一次关闭新文件时设置的文件的权限设置。 否则为*pmode*将被忽略。 *pmode*是一个包含一个或两个清单常量的整数表达式 **_S_IWRITE**和 **_S_IREAD**，其定义中\<sys\stat.h >。 当给定这两个常量时，将使用按位“或”运算符合并它们。 含义*pmode*如下。

|*pmode*|含义|
|-|-|
**_S_IREAD**|只允许读取。
**_S_IWRITE**|允许写入。 （实际上，允许读取和写入。）
**_S_IREAD** &AMP;#124; **_S_IWRITE**|允许读取和写入。

如果未授予写入权限，则该文件为只读。 在 Windows 操作系统中，所有文件均可读；不可能提供只写权限。 因此，模式 **_S_IWRITE**和 **_S_IREAD** | **_S_IWRITE**是等效的。

**_sopen**将当前文件权限掩码应用到*pmode*之前设置了权限。 （请参阅 [_umask](umask.md)。）

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|
|**_wsopen**|\<io.h> 或 \<wchar.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_locking](locking.md) 的示例。

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[_fsopen、_wfsopen](fsopen-wfsopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
