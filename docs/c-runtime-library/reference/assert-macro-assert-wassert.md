---
title: assert 宏、_assert、_wassert | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- assert
- _assert
- _wassert
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1d2bef607e80e2e972915bd8a8b0517b7c6e5eb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200662"
---
# <a name="assert-macro-assert-wassert"></a>assert 宏、_assert、_wassert

计算表达式，如果结果为**false**，输出诊断消息并中止程序。

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

*表达式*计算结果不为零的标量表达式 （包括指针表达式） (**true**) 或 0 (**false**)。

*消息*要显示的消息。

*文件名*文件中的失败的断言的源的名称。

*行*失败的断言的源文件中的行号。

## <a name="remarks"></a>备注

**断言**宏通常用于标识程序开发过程的逻辑错误。 使用它来通过实现出现意外的情况时停止程序执行*表达式*参数来计算**false**仅当程序操作不正确。 断言检查也会关闭在编译时通过定义宏**NDEBUG**。 你可以关闭**断言**宏，而无需通过使用修改的源文件 **/DNDEBUG**命令行选项。 你可以关闭**断言**通过使用在源代码中的宏`#define NDEBUG`指令之前\<assert.h > 包含。

**断言**宏打印诊断消息何时*表达式*计算结果为**false** (0) 和调用[中止](abort.md)终止程序执行。 如果不执行任何操作*表达式*是**true** （非零）。 诊断消息包括失败的表达式、源文件的名称以及断言失败的行号。

诊断消息将用宽字符打印。 因此，它将按预期工作，即使表达式中存在 Unicode 字符也是如此。

诊断消息的目标取决于调用例程的应用程序的类型。 控制台应用程序一定会收到消息传递**stderr**。 在基于 Windows 的应用程序中，**断言**调用 Windows [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox)函数来创建一个消息框显示消息以及**确定**按钮。 当用户单击 **“确定”** 后，程序将立即中止。

当与运行时库的调试版本链接应用程序**断言**创建带三个按钮的消息框：**中止**，**重试**，以及**忽略**。 如果用户单击 **“中止”**，则程序将立即中止。 如果用户单击 **“重试”**，则将调用调试器，之后用户可以调试程序，前提是启用了实时 (JIT) 调试。 如果用户单击**忽略**，**断言**继续其常规执行： 创建具有消息框**确定**按钮。 请注意，当存在错误条件时单击 **“忽略”** 可能导致未定义的行为。

有关 CRT 调试的详细信息，请参阅 [CRT 调试技术](/visualstudio/debugger/crt-debugging-techniques)。

**_Assert**并 **_wassert**函数是内部 CRT 函数。 这两个函数可帮助最大程度地减少在对象文件中支持断言所需的代码。 建议不要直接调用这些函数。

**断言**C 运行时库的发行版和调试版本中启用宏时**NDEBUG**未定义。 当**NDEBUG**是定义，该宏是可用，但不会评估其参数和不起作用。 启用后，**断言**宏调用 **_wassert**其实现。 其他断言宏 [_ASSERT](assert-asserte-assert-expr-macros.md)、[_ASSERTE](assert-asserte-assert-expr-macros.md) 和 [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md) 也可用，但它们只有在已定义 [_DEBUG](../../c-runtime-library/debug.md) 宏的情况下以及存在于与 C 运行时库调试版本关联的代码中时才会计算传递给它们的表达式。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**断言**， **_wassert**|\<assert.h>|

签名 **_assert**函数头文件中不可用。 签名 **_wassert**时，函数才可用**NDEBUG**未定义宏。

## <a name="example"></a>示例

在此程序中， **analyze_string**函数使用**断言**与字符串和长度相关的宏来测试多个条件。 如果任意条件失败，则程序将打印指示失败原因的消息。

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

如果已安装调试器，请选择“调试”  按钮以启动调试器，或选择“关闭程序”  以退出。

## <a name="see-also"></a>请参阅

[错误处理](../../c-runtime-library/error-handling-crt.md)<br/>
[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
