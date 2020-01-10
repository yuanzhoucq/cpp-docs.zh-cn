---
title: C++程序终止
ms.date: 12/10/2019
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
ms.openlocfilehash: a0e86cacd951327d39296a183be5ee4fbc36fd15
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301335"
---
# <a name="c-program-termination"></a>C++程序终止

在C++中，可以通过以下方式退出节目：

- 调用[exit](exit-function.md)函数。
- 调用[abort](abort-function.md)函数。
- 执行 `main`的[return](return-statement-cpp.md)语句。

## <a name="exit-function"></a>exit 函数

[Exit](../c-runtime-library/reference/exit-exit-exit.md)函数在 \<stdlib.h > 中声明，用于C++终止程序。 作为 `exit` 的参数提供的值将作为程序的返回代码或退出代码返回到操作系统。 按照约定，返回代码为零表示该程序已成功完成。 您可以使用 EXIT_FAILURE 和 EXIT_SUCCESS 中定义的常量，\<stdlib.h > 中指定程序的成功或失败。

从 `main` 函数发出**return**语句等效于使用返回值作为参数来调用 `exit` 函数。

## <a name="abort-function"></a>abort 函数

[中止](../c-runtime-library/reference/abort.md)函数，同样在标准包含文件中声明\<stdlib.h >，将终止 C++ 程序。 `exit` 和 `abort` 之间的区别在于 `exit` 允许进行C++运行时终止处理（将调用全局对象析构函数），而 `abort` 会立即终止程序。 `abort` 函数将绕过已初始化全局静态对象的正常析构进程。 它还会绕过使用[atexit](../c-runtime-library/reference/atexit.md)函数指定的任何特殊处理。

## <a name="atexit-function"></a>atexit 函数

使用[atexit](../c-runtime-library/reference/atexit.md)函数指定在程序终止之前执行的操作。 在执行退出处理函数之前，不会销毁对**atexit**的调用之前初始化的全局静态对象。

## <a name="return-statement-in-main"></a>main 中的 return 语句

发出 `main` 的[return](return-statement-cpp.md)语句在功能上等同于调用 `exit` 函数。 请看下面的示例：

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

上一示例中的 `exit` 和**return**语句的功能相同。 但是， C++要求具有**void**以外的返回类型的函数返回一个值。 **Return**语句允许从 `main`返回值。

## <a name="destruction-of-static-objects"></a>静态对象的析构

调用 `exit` 或从 `main`执行**return**语句时，静态对象将按其初始化的反向顺序销毁（在调用 `atexit` （如果存在）之后。 以下示例演示如何进行此类初始化和清理工作。

### <a name="example"></a>示例

在下面的示例中，将在进入 `main`之前创建并初始化静态对象 `sd1` 和 `sd2`。 在此程序使用**return**语句终止后，第一个 `sd2` 被销毁，然后 `sd1`。 `ShowData` 类的析构函数将关闭与这些静态对象关联的文件。

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

[main：程序启动](main-program-startup.md)