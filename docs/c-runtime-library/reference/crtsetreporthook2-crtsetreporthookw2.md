---
title: _CrtSetReportHook2、_CrtSetReportHookW2 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetReportHook2
- _CrtSetReportHookW2
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
- CrtSetReportHookW2
- CrtSetReportHook2
- _CrtSetReportHookW2
- _CrtSetReportHook2
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportHook2 function
- _CrtSetReportHook2 function
- _CrtSetReportHookW2 function
- CrtSetReportHookW2 function
ms.assetid: 12e5f68d-c8a7-4b1a-9a75-72ba4a8592d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17dc0fc97a46e6ce0b5bda68ec8adc6ef37c4218
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetreporthook2-crtsetreporthookw2"></a>_CrtSetReportHook2、_CrtSetReportHookW2

通过以下方式安装或卸载客户端定义的报告函数：将该函数挂钩到 C 运行时调试报告过程（仅限调试版本）中。

## <a name="syntax"></a>语法

```C
int _CrtSetReportHook2(
   int mode,
   _CRT_REPORT_HOOK pfnNewHook
);
int _CrtSetReportHookW2(
   int mode,
   _CRT_REPORT_HOOKW pfnNewHook
);
```

### <a name="parameters"></a>参数

*模式*<br/>
要执行的操作： **_CRT_RPTHOOK_INSTALL**或 **_CRT_RPTHOOK_REMOVE**。

*pfnNewHook*<br/>
若要安装或删除此函数的窄字符或宽字符版本中的报告挂钩。

## <a name="return-value"></a>返回值

如果遇到错误，则为-1 与**EINVAL**或**ENOMEM**设置; 否则将返回的引用计数*pfnNewHook*后调用。

## <a name="remarks"></a>备注

**_CrtSetReportHook2**和 **_CrtSetReportHookW2**让您能够挂钩或解除挂钩函数，而[_CrtSetReportHook](crtsetreporthook.md)仅能让您挂钩函数。

**_CrtSetReportHook2**或 **_CrtSetReportHookW2**应而不是使用 **_CrtSetReportHook**时在 DLL 中进行挂钩调用而可能在多个 Dll 加载时，并设置其自己挂钩函数。 在此类情况下，可按与 DLL 的加载顺序不同的顺序来卸载 DLL，并且挂钩函数可以仍指向已卸载的 DLL。 任何调试输出会导致进程崩溃如果通过添加了挂钩函数 **_CrtSetReportHook**。

任何挂钩函数与添加 **_CrtSetReportHook**如果未将函数添加与调用 **_CrtSetReportHook2**或 **_CrtSetReportHookW2**或如果所有挂钩函数将与添加 **_CrtSetReportHook2**和 **_CrtSetReportHookW2**返回**FALSE**。

此函数的宽字符版本可用。 报告挂钩函数采用一个其类型（宽字符或窄字符）必须与使用的此函数版本匹配的字符串。 将以下函数原型用于与此函数的宽字符版本一起使用的报告挂钩：

```C
int YourReportHook( int reportType, wchar_t *message, int *returnValue );
```

将以下原型用于窄字符报告挂钩：

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

这些函数验证其参数。 如果*模式*或**pfnNewNook**是无效的这些函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回-1。

> [!NOTE]
> 如果你的应用程序进行编译的 **/clr**和报告的函数调用后已退出应用程序主，CLR 将引发异常，如果报告的函数调用任何 CRT 函数。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_CrtSetReportHook2**|\<crtdbg.h>|\<errno.h>|
|**_CrtSetReportHookW2**|\<crtdbg.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

```C
// crt_setreporthook2.c
#include <windows.h>
#include <stdio.h>
#include <crtdbg.h>
#include <assert.h>

int __cdecl TestHook1(int nReportType, char* szMsg, int* pnRet)
{
   int nRet = FALSE;

   printf("CRT report hook 1.\n");
   printf("CRT report type is \"");
   switch (nReportType)
   {
      case _CRT_ASSERT:
      {
         printf("_CRT_ASSERT");
         // nRet = TRUE;   // Always stop for this type of report
         break;
      }

      case _CRT_WARN:
      {
         printf("_CRT_WARN");
         break;
      }

      case _CRT_ERROR:
      {
         printf("_CRT_ERROR");
         break;
      }

      default:
      {
         printf("???Unknown???");
         break;
      }
   }

   printf("\".\nCRT report message is:\n\t");
   printf(szMsg);

   if   (pnRet)
      *pnRet = 0;

   return   nRet;
}

int __cdecl   TestHook2(int nReportType, char* szMsg, int* pnRet)
{
   int   nRet = FALSE;

   printf("CRT report hook 2.\n");
   printf("CRT report type is \"");
   switch   (nReportType)
   {
      case _CRT_WARN:
      {
         printf("_CRT_WARN");
         break;
      }

      case _CRT_ERROR:
      {
         printf("_CRT_ERROR");
         break;
      }

      case _CRT_ASSERT:
      {
         printf("_CRT_ASSERT");
         nRet = TRUE;   // Always stop for this type of report
         break;
      }

      default:
      {
         printf("???Unknown???");
         break;
      }
   }

   printf("\".\nCRT report message is: \t");
   printf(szMsg);

   if   (pnRet)
      *pnRet = 0;
   // printf("CRT report code is %d.\n", *pnRet);
   return   nRet;
}

int   main(int argc, char* argv[])
{
   int   nRet = 0;

   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"
          " returned %d\n", nRet);

   _ASSERT(0);

   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"
          " returned %d\n", nRet);

   return   nRet;
}
```

### <a name="output"></a>输出

```Output
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0
```

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
