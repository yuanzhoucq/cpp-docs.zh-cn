---
title: C + + 程序终止
description: '介绍 :::no-loc(exit)::: c + + 语言程序的方式。'
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- :::no-loc(exit):::ing applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- ':::no-loc(exit):::'
- ':::no-loc(abort):::'
- ':::no-loc(return):::'
- ':::no-loc(main):::'
- ':::no-loc(atexit):::'
- ':::no-loc(void):::'
ms.openlocfilehash: 216aef5dbe8d110f9d75d43b5009b89fc5bfda51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227174"
---
# <a name="c-program-termination"></a>C + + 程序终止

在 c + + 中，可以通过 :::no-loc(exit)::: 以下方式使用程序：

- 调用 [:::no-loc(exit):::](:::no-loc(exit):::-function.md) 函数。
- 调用 [:::no-loc(abort):::](:::no-loc(abort):::-function.md) 函数。
- 从执行 [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) 语句 `:::no-loc(main):::` 。

## <a name="no-locexit-function"></a>:::no-loc(exit)::: 函数

[:::no-loc(exit):::](../c-runtime-library/reference/:::no-loc(exit):::-:::no-loc(exit):::-:::no-loc(exit):::.md)在中声明的函数 \<stdlib.h> 终止 c + + 程序。 作为的参数提供的值 `:::no-loc(exit):::` 是 :::no-loc(return)::: 作为程序的 :::no-loc(return)::: 代码或代码的操作系统 :::no-loc(exit)::: 。 按照约定，如果 :::no-loc(return)::: 代码为零，则表示程序已成功完成。 您可以使用 EXIT_FAILURE 和 EXIT_SUCCESS 中定义的常量 \<stdlib.h> 来指示程序是成功还是失败。

**`:::no-loc(return):::`** 从函数发出语句 `:::no-loc(main):::` 等效于 `:::no-loc(exit):::` 使用 :::no-loc(return)::: 值作为其参数调用函数。

## <a name="no-locabort-function"></a>:::no-loc(abort)::: 函数

[:::no-loc(abort):::](../c-runtime-library/reference/:::no-loc(abort):::.md)还在标准包含文件中声明的函数 \<stdlib.h> 终止 c + + 程序。 与之间的区别在于 `:::no-loc(exit):::` `:::no-loc(abort):::` 允许进行 `:::no-loc(exit):::` c + + 运行时终止处理（将调用全局对象析构函数），而是 `:::no-loc(abort):::` 立即终止程序。 `:::no-loc(abort):::`函数会绕过已初始化全局静态对象的正常析构进程。 它还会绕过函数指定的任何特殊处理 [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) 。

## <a name="no-locatexit-function"></a>:::no-loc(atexit)::: 函数

使用 [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) 函数指定在程序终止之前执行的操作。 在 **:::no-loc(atexit):::** 执行 :::no-loc(exit)::: -处理函数之前，不会对调用之前初始化的全局静态对象进行销毁。

## <a name="no-locreturn-statement-in-no-locmain"></a>:::no-loc(return):::语句:::no-loc(main):::

发出的 [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) 语句 `:::no-loc(main):::` 在功能上等效于调用 `:::no-loc(exit):::` 函数。 请考虑以下示例：

```cpp
// :::no-loc(return):::_statement.cpp
#include <stdlib.h>
int :::no-loc(main):::()
{
    :::no-loc(exit):::( 3 );
    :::no-loc(return)::: 3;
}
```

`:::no-loc(exit):::`前面的 **`:::no-loc(return):::`** 示例中的和语句在功能上相同。 但是，c + + 要求 :::no-loc(return)::: 类型不 **`:::no-loc(void):::`** :::no-loc(return)::: 是值的函数。 **`:::no-loc(return):::`** 语句允许 :::no-loc(return)::: 使用中的值 `:::no-loc(main):::` 。

## <a name="destruction-of-static-objects"></a>静态对象的析构

当从调用 `:::no-loc(exit):::` 或执行 **`:::no-loc(return):::`** 语句时 `:::no-loc(main):::` ，静态对象会按其初始化的反向顺序销毁（调用后， `:::no-loc(atexit):::` 如果存在）。 以下示例演示如何进行此类初始化和清理工作。

### <a name="example"></a>示例

在下面的示例中，将在 `sd1` `sd2` 进入之前创建并初始化静态对象和 `:::no-loc(main):::` 。 此程序使用语句终止后 **`:::no-loc(return):::`** ，首先 `sd2` 销毁，然后再销毁 `sd1` 。 `ShowData` 类的析构函数将关闭与这些静态对象关联的文件。

```cpp
// using_:::no-loc(exit):::_or_:::no-loc(return):::1.cpp
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
   :::no-loc(void)::: Disp( char *szData ) {
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

int :::no-loc(main):::() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

另一种编写此代码的方式为，使用块范围声明 `ShowData` 对象，并允许在它们超出范围时将其销毁：

```cpp
int :::no-loc(main):::() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>另请参阅

[:::no-loc(main):::函数和命令行参数](:::no-loc(main):::-function-command-line-args.md)
