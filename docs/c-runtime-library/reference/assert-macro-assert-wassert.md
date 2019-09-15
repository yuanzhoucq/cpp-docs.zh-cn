---
title: assert 宏、_assert、_wassert
ms.date: 11/04/2016
api_name:
- assert
- _assert
- _wassert
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
ms.openlocfilehash: badca46a0793e51602f0de87dfca21816dcd6295
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939620"
---
# <a name="assert-macro-_assert-_wassert"></a>assert 宏、_assert、_wassert

计算表达式，如果结果为**false**，则打印诊断消息并中止程序。

## <a name="syntax"></a>语法

```C
assert(
   expression
);
void _assert(
   char const* message,
   char const* filename,
   unsigned line
);
void _wassert(
   wchar_t const* message,
   wchar_t const* filename,
   unsigned line
);
```

### <a name="parameters"></a>参数

expression<br/>
计算结果为非零值（**true**）或0（**false**）的标量表达式（包括指针表达式）。

*message*<br/>
要显示的消息。

*filename*<br/>
断言失败的源文件的名称。

*line*<br/>
断言失败处所在的源文件行号。

## <a name="remarks"></a>备注

**断言**宏通常用于标识程序开发过程中的逻辑错误。 如果出现意外情况，请使用它来停止程序执行，方法是实现*表达式*参数，使其在程序运行不正常时计算为**false** 。 通过定义宏**NDEBUG**，可以在编译时关闭断言检查。 您可以通过使用 **/DNDEBUG**命令行选项来关闭**断言**宏，而无需修改您的源文件。 可以通过在包含 assert > 之前`#define NDEBUG` \<使用指令在源代码中关闭断言宏。

如果*表达式*的计算结果为**false** （0），则**assert**宏将打印诊断消息，并调用[abort](abort.md)终止程序执行。 如果*expression*为**true** （非零），则不执行任何操作。 诊断消息包括失败的表达式、源文件的名称以及断言失败的行号。

诊断消息将用宽字符打印。 因此，它将按预期工作，即使表达式中存在 Unicode 字符也是如此。

诊断消息的目标取决于调用例程的应用程序的类型。 控制台应用程序始终通过**stderr**接收消息。 在基于 Windows 的应用程序中， **assert**调用 Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)函数以创建消息框，同时显示消息以及 **"确定"** 按钮。 当用户单击 **“确定”** 后，程序将立即中止。

当应用程序与调试版的运行时库链接时，**断言**会创建一个包含三个按钮的消息框：**Abort**、 **Retry**和**Ignore**。 如果用户单击 **“中止”** ，则程序将立即中止。 如果用户单击 **“重试”** ，则将调用调试器，之后用户可以调试程序，前提是启用了实时 (JIT) 调试。 如果用户单击 "**忽略**"，则**断言**将继续执行其常规执行：创建包含 **"确定"** 按钮的消息框。 请注意，当存在错误条件时单击 **“忽略”** 可能导致未定义的行为。

有关 CRT 调试的详细信息，请参阅 [CRT 调试技术](/visualstudio/debugger/crt-debugging-techniques)。

**_Assert**和 **_wassert**函数是内部 CRT 函数。 这两个函数可帮助最大程度地减少在对象文件中支持断言所需的代码。 建议不要直接调用这些函数。

如果未定义**NDEBUG** ，则在 C 运行库的发布版本和调试版本中均启用**断言**宏。 定义**NDEBUG**后，宏可用，但不会计算其自变量，并且不起作用。 启用后， **assert**宏将为其实现调用 **_wassert** 。 其他断言宏 [_ASSERT](assert-asserte-assert-expr-macros.md)、 [_ASSERTE](assert-asserte-assert-expr-macros.md) 和 [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md)也可用，但它们只有在已定义 [_DEBUG](../../c-runtime-library/debug.md) 宏的情况下以及存在于与 C 运行时库调试版本关联的代码中时才会计算传递给它们的表达式。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**assert**、 **_wassert**|\<assert.h>|

**_Assert**函数的签名在头文件中不可用。 仅当未定义**NDEBUG**宏时， **_wassert**函数的签名才可用。

## <a name="example"></a>示例

在此程序中， **analyze_string**函数使用**assert**宏来测试与字符串和长度相关的一些条件。 如果任意条件失败，则程序将打印指示失败原因的消息。

```C
// crt_assert.c
// compile by using: cl /W4 crt_assert.c
#include <stdio.h>
#include <assert.h>
#include <string.h>

void analyze_string( char *string );   // Prototype

int main( void )
{
   char  test1[] = "abc", *test2 = NULL, test3[] = "";

   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );
   analyze_string( test1 );
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );
   analyze_string( test2 );
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );
   analyze_string( test3 );
}

// Tests a string to see if it is NULL,
// empty, or longer than 0 characters.
void analyze_string( char * string )
{
   assert( string != NULL );        // Cannot be NULL
   assert( *string != '\0' );       // Cannot be empty
   assert( strlen( string ) > 2 );  // Length must exceed 2
}
```

该程序会生成以下输出：

```Output
Analyzing string 'abc'
Analyzing string '(null)'
Assertion failed: string != NULL, file crt_assert.c, line 25
```

断言失败后，可能会看到一个包含如下内容的消息框（具体取决于操作系统和运行时库的版本）：

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

如果已安装调试器，请选择“调试” 按钮以启动调试器，或选择“关闭程序” 以退出。

## <a name="see-also"></a>请参阅

[错误处理](../../c-runtime-library/error-handling-crt.md)<br/>
[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
