---
title: _CrtSetReportFile
ms.date: 11/04/2016
apiname:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: 32a560e09c47468daf48c185e23d6e289c6d1d9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464241"
---
# <a name="crtsetreportfile"></a>_CrtSetReportFile

在使用后[_CrtSetReportMode](crtsetreportmode.md)来指定 **_CRTDBG_MODE_FILE**，可以指定要接收的消息文本的文件句柄。 **_CrtSetReportFile**也可由[_CrtDbgReport、 _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)以指定文本 （仅限调试版本） 的目标。

## <a name="syntax"></a>语法

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>参数

*reportType*<br/>
报告类型： **_CRT_WARN**， **_CRT_ERROR**，并 **_CRT_ASSERT**。

*reportFile*<br/>
新的报表文件*reportType*。

## <a name="return-value"></a>返回值

成功完成后， **_CrtSetReportFile**返回先前的报表文件中指定的报告类型定义*reportType*。 如果为传入的无效值*reportType*，此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**并且该函数返回 **_CRTDBG_HFILE_ERROR**。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_CrtSetReportFile**用于[_CrtSetReportMode](crtsetreportmode.md)函数来定义的目标或目标的生成的特定报表类型 **_CrtDbgReport**。 当 **_CrtSetReportMode**已调用来分配 **_CRTDBG_MODE_FILE**报告模式的特定报表类型， **_CrtSetReportFile**然后应调用到定义特定文件或流要用作目标。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtSetReportFile**在预处理过程中删除。

以下列表显示的可用选项*reportFile*和产生的行为 **_CrtDbgReport**。 在 Crtdbg.h 中将这些选项定义为位标志。

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

   将消息写入**stderr**，可定向，如下所示：

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   将消息写入**stdout**，可进行重定向。

- **_CRTDBG_REPORT_FILE**

   返回当前报告模式。

可以单独控制每种报告类型所使用的报表文件。 例如，它是可以指定*reportType*的 **_CRT_ERROR**报告给**stderr**，而*reportType* 的 **_CRT_ASSERT**报告给用户定义的文件句柄或流。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 控制台中，与关联的标准流句柄**stdin**， **stdout**，并**stderr**，C 运行时函数可以在 UWP 应用中使用它们之前，必须重定向. 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库：** 仅限 [CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
