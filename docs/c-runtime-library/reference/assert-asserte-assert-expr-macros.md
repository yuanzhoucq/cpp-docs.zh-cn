---
title: _ASSERT、_ASSERTE、_ASSERT_EXPR 宏 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
- _ASSERTE
- ASSERTE
- _ASSERT
- _ASSERT_EXPR
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a089017b38d27130883bb091190e92d2b1e3469
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="assert-asserte-assertexpr-macros"></a>_ASSERT、_ASSERTE、_ASSERT_EXPR 宏

计算表达式，并生成调试报告，如果结果为**False** （仅限调试版本）。

## <a name="syntax"></a>语法

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>参数

*布尔表达式*的计算结果为非零 (true) 或 0 (false) 的标量表达式 （包括指针表达式）。

*消息*宽字符串显示为报表的一部分。

## <a name="remarks"></a>备注

**_ASSERT_EXPR**， **_ASSERT**和 **_ASSERTE**宏提供清楚、 简单的机制，用于在调试过程中检查假设提供的应用程序。 它们非常灵活，因为无需包含在 `#ifdef` 语句中，可防止在零售版本的应用程序中调用它们。 这种灵活性使用 [_DEBUG](../../c-runtime-library/debug.md) 宏来实现。 **_ASSERT_EXPR**， **_ASSERT**和 **_ASSERTE**时，将仅可用 **_DEBUG**在编译时定义。 当 **_DEBUG**是未定义，对这些宏的调用将删除在预处理过程。

**_ASSERT_EXPR**， **_ASSERT**和 **_ASSERTE**评估其*布尔表达式*自变量和结果时**false**(0)，它们会打印诊断消息并调用[_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)生成调试报告。 **_ASSERT**宏将打印简单的诊断消息， **_ASSERTE**在消息中，包括的字符串表示形式失败表达式和 **_ASSERT_EXPR**包括*消息*诊断消息中的字符串。 这些宏不执行任何操作时*布尔表达式*计算结果为非零。

**_ASSERT_EXPR**， **_ASSERT**和 **_ASSERTE**调用 **_CrtDbgReportW**，这将导致所有输出都采用宽字符。 **_ASSERTE**正确打印 Unicode 字符在*布尔表达式*和 **_ASSERT_EXPR**输出中的 Unicode 字符*消息*。

因为 **_ASSERTE**宏会指定失败的表达式，和 **_ASSERT_EXPR**可让你在生成的报告指定消息，所以它们使用户可以识别问题，而不会引用应用程序源代码。 但是，存在一个缺点在于每个*消息*打印的 **_ASSERT_EXPR**和通过计算每个表达式 **_ASSERTE**输出 （调试版本） 中包含应用程序将作为字符串常量的文件。 因此，如果大量的调用以及供 **_ASSERT_EXPR**或 **_ASSERTE**，这些表达式可以大大增加输出文件的大小。

除非使用 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函数另行指定，否则消息会出现在弹出对话框中，这等于设置以下内容：

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW**生成调试报告并确定其目标或目标，基于当前报告模式或模式和文件为定义 **_CRT_ASSERT**报告类型。 默认情况下，断言失败和错误会定向到调试消息窗口。 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函数用于为每种报告类型定义目标。

当目标是调试消息窗口和用户单击**重试**按钮， **_CrtDbgReportW**返回 1，从而导致 **_ASSERT_EXPR**， **_断言**和 **_ASSERTE**宏启动调试器，前提是启用了实时 (JIT) 调试。

有关报告过程的详细信息，请参阅 [_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) 函数。 有关解决断言失败以及将这些宏用作调试错误处理机制的详细信息，请参阅 [使用宏进行验证和报告](/visualstudio/debugger/macros-for-reporting)。

除了 **_ASSERT**宏，[断言](assert-macro-assert-wassert.md)宏可以用于验证程序逻辑。 此宏可在这些库的调试和发布版本中使用。 [_RPT、_RPTF](rpt-rptf-rptw-rptfw-macros.md) 调试宏还可用于生成调试报告，但它们不计算表达式。 **_RPT**宏生成一个简单的报表。 **_RPTF**宏在生成的报告包括其中调用报告宏的源文件和行号。 提供了这些宏的宽字符版本 (**_RPTW**， **_RPTFW**)。 宽字符版本与窄字符版本相同，只不过宽字符字符串用于所有字符串参数和输出。

尽管 **_ASSERT_EXPR**， **_ASSERT**和 **_ASSERTE**是宏并且可通过包含\<b g.h >，应用程序必须与调试链接C 运行时库的版本时 **_DEBUG**因为这些宏调用其他运行时函数定义。

## <a name="requirements"></a>要求

|宏|必需的标头|
|-----------|---------------------|
|**_ASSERT_EXPR**， **_ASSERT**， **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>示例

在此程序中，则对进行调用 **_ASSERT**和 **_ASSERTE**宏，以测试条件`string1 == string2`。 如果条件失败，则这些宏会打印诊断消息。 **_RPT**和 **_RPTF**宏组中还会执行此程序中，作为替代方法**printf**函数。

```C
// crt_ASSERT_macro.c
// compile with: /D_DEBUG /MTd /Od /Zi /link /verbose:lib /debug
//
// This program uses the _ASSERT and _ASSERTE debugging macros.
//

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main()
{
   char *p1, *p2;

   // The Reporting Mode and File must be specified
   // before generating a debug report via an assert
   // or report macro.
   // This program sends all report types to STDOUT.
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ASSERT, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ASSERT, _CRTDBG_FILE_STDOUT);

   // Allocate and assign the pointer variables.
   p1 = (char *)malloc(10);
   strcpy_s(p1, 10, "I am p1");
   p2 = (char *)malloc(10);
   strcpy_s(p2, 10, "I am p2");

   // Use the report macros as a debugging
   // warning mechanism, similar to printf.
   // Use the assert macros to check if the
   // p1 and p2 variables are equivalent.
   // If the expression fails, _ASSERTE will
   // include a string representation of the
   // failed expression in the report.
   // _ASSERT does not include the
   // expression in the generated report.
   _RPT0(_CRT_WARN,
       "Use the assert macros to evaluate the expression p1 == p2.\n");
   _RPTF2(_CRT_WARN, "\n Will _ASSERT find '%s' == '%s' ?\n", p1, p2);
   _ASSERT(p1 == p2);

   _RPTF2(_CRT_WARN, "\n\n Will _ASSERTE find '%s' == '%s' ?\n",
          p1, p2);
   _ASSERTE(p1 == p2);

   _RPT2(_CRT_ERROR, "'%s' != '%s'\n", p1, p2);

   free(p2);
   free(p1);

   return 0;
}
```

```Output
Use the assert macros to evaluate the expression p1 == p2.
crt_ASSERT_macro.c(54) :
Will _ASSERT find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(55) : Assertion failed!
crt_ASSERT_macro.c(58) :

Will _ASSERTE find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2
'I am p1' != 'I am p2'
```

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[assert 宏、_assert、_wassert](assert-macro-assert-wassert.md)<br/>
[_RPT、_RPTF、_RPTW、_RPTFW 宏](rpt-rptf-rptw-rptfw-macros.md)<br/>
