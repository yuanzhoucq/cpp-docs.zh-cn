---
title: C++程序终止
description: 介绍 exit C++语言程序的方式。
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- exit
- abort
- return
- main
- atexit
- void
ms.openlocfilehash: f83c9d5da5b0a1127603a97fd7946e9cca43a7a5
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123950"
---
# <a name="c-program-termination"></a>C++程序终止

在C++中，可以通过以下方式 exit 程序：

- 调用[exit](exit-function.md)函数。
- 调用[abort](abort-function.md)函数。
- 从 `main`执行[return](return-statement-cpp.md)语句。

## <a name="opno-locexit-function"></a>exit 函数

\<stdlib.h > 中声明的[exit](../c-runtime-library/reference/exit-exit-exit.md)函数终止C++程序。 作为 `exit` 的参数提供的值将作为程序的 return 代码或 exit 代码返回到操作系统。 按照约定，return 的代码为零，则表示程序已成功完成。 您可以使用 EXIT_FAILURE 和 EXIT_SUCCESS 中定义的常量，\<stdlib.h > 中指定程序的成功或失败。

从 `main` 函数发出 **return** 语句等效于使用 return 值作为参数来调用 `exit` 函数。

## <a name="opno-locabort-function"></a>abort 函数

[abort](../c-runtime-library/reference/abort.md)函数（也在标准包含文件 \<stdlib.h > 中声明）终止C++程序。 `exit` 和 `abort` 之间的区别在于 `exit` 允许进行C++运行时终止处理（将调用全局对象析构函数），而 `abort` 会立即终止程序。 `abort` 函数将绕过已初始化全局静态对象的正常析构进程。 它还会绕过使用[atexit](../c-runtime-library/reference/atexit.md)函数指定的任何特殊处理。

## <a name="opno-locatexit-function"></a>atexit 函数

使用[atexit](../c-runtime-library/reference/atexit.md)函数指定在程序终止之前执行的操作。 在执行 exit处理函数之前，不会销毁在调用 **atexit** 之前初始化的全局静态对象。

## <a name="opno-locreturn-statement-in-opno-locmain"></a>main 中的 return 语句

从 `main` 发出[return](return-statement-cpp.md)语句在功能上等效于调用 `exit` 函数。 请看下面的示例：

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

上一示例中的 `exit` 和 **return** 语句功能完全相同。 但是， C++要求具有除 **void** 以外 return 类型 return 值的函数。 **return** 语句允许您从 `main`中 return 值。

## <a name="destruction-of-static-objects"></a>静态对象的析构

调用 `exit` 或从 `main`执行 **return** 语句时，静态对象会按其初始化的反向顺序销毁（在调用 `atexit` （如果存在）之后。 以下示例演示如何进行此类初始化和清理工作。

### <a name="example"></a>示例

在下面的示例中，将在进入 `main`之前创建并初始化静态对象 `sd1` 和 `sd2`。 此程序使用 **return** 语句终止后，首先 `sd2` 销毁，然后 `sd1`。 `ShowData` 类的析构函数将关闭与这些静态对象关联的文件。

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

另一种编写此代码的方式为，使用块范围声明 `ShowData` 对象，并允许在它们超出范围时将其销毁：

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>另请参阅

[main 函数和命令行参数](main-function-command-line-args.md)
