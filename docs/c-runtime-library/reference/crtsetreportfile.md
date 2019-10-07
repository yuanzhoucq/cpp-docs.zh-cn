---
title: _CrtSetReportFile
ms.date: 11/04/2016
api_name:
- _CrtSetReportFile
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: bf88bae40031f6e92d6f936ac8a50f85d6c4e36c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942281"
---
# <a name="_crtsetreportfile"></a>_CrtSetReportFile

使用[_CrtSetReportMode](crtsetreportmode.md)指定 **_CRTDBG_MODE_FILE**后，可以指定接收消息文本的文件句柄。 [_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)还使用 **_CrtSetReportFile**来指定文本的目标（仅限调试版本）。

## <a name="syntax"></a>语法

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>参数

*reportType*<br/>
报表类型： **_CRT_WARN**、 **_CRT_ERROR**和 **_CRT_ASSERT**。

*reportFile*<br/>
新的*reportType*报表文件。

## <a name="return-value"></a>返回值

成功完成后， **_CrtSetReportFile**将返回为*reportType*中指定的报表类型定义的上一个报表文件。 如果为*reportType*传入了无效的值，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且函数将返回 **_CRTDBG_HFILE_ERROR**。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_CrtSetReportFile**用于[_CrtSetReportMode](crtsetreportmode.md)函数来定义 **_CrtDbgReport**生成的特定报表类型的目标。 如果已调用 **_CrtSetReportMode**为特定的报表类型分配 **_CRTDBG_MODE_FILE**报表模式，则应该调用 **_CrtSetReportFile**来定义要用作目标的特定文件或流。 未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtSetReportFile**的调用。

以下列表显示了*reportFile*的可用选项，以及 **_CrtDbgReport**的结果行为。 在 Crtdbg.h 中将这些选项定义为位标志。

- **文件句柄**

   将作为消息目标的文件的句柄。 不会尝试验证该句柄的有效性。 必须打开并关闭该文件的句柄。 例如：

   ```C
   HANDLE hLogFile;
   hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,
      FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,
      FILE_ATTRIBUTE_NORMAL, NULL);
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, hLogFile);

   _RPT0(_CRT_WARN,"file message\n");
   CloseHandle(hLogFile);
   ```

- **_CRTDBG_FILE_STDERR**

   将消息写入**stderr**，可以按如下方式重定向：

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   将消息写入**stdout**，可以重定向。

- **_CRTDBG_REPORT_FILE**

   返回当前报告模式。

可以单独控制每种报告类型所使用的报表文件。 例如，可以指定将 **_CRT_ERROR**的*reportType*报告给**stderr**，同时向用户定义的文件句柄或流报告 **_CRT_ASSERT**的*reportType* 。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 与控制台、 **stdin**、 **stdout**和**stderr**关联的标准流句柄必须重定向, 然后 C 运行时函数才能在 UWP 应用中使用它们。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库**仅限[CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
