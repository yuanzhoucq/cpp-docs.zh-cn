---
title: 跨 DLL 边界传递 CRT 对象时可能的错误
ms.date: 11/04/2016
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: 10fbb128698b6422779d09a15fe3c1d25e8de5b5
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446651"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>跨 DLL 边界传递 CRT 对象时可能的错误

当你将 C 运行时 (CRT) 对象（例如，文件句柄、区域设置和环境变量）传入或传出 DLL（跨 DLL 边界的函数调用）时，如果 DLL 以及 DLL 中调用的文件使用不同的 CRT 库副本，则可能发生意外行为。

如果你分配内存（使用 `new` 或 `malloc` 显式分配，或使用 `strdup`、`strstreambuf::str` 等隐式分配），然后跨 DLL 边界传递要释放的指针，则会出现相关问题。 如果 DLL 及其用户使用不同的 CRT 库副本，则会导致内存访问冲突或堆损坏。

调试期间，此问题的另一种症状可能是输出窗口中的错误，例如：

HEAP[]：针对 RtlValidateHeap(#,#) 指定的地址无效

## <a name="causes"></a>原因

CRT 库的每个副本都具有单独且完全不同的状态，且按应用或 DLL 保存于线程本地存储中。 因此，CRT 对象（例如，文件句柄、环境变量和区域设置）仅对在其中分配或设置这些对象的 CRT 的应用或 DLL 的副本有效。 当 DLL 及其应用客户端使用不同的 CRT 库副本时，你无法跨 DLL 边界传递这些 CRT 对象，也无法期望在另一侧正确地选取它们。 这对 Visual Studio 2015 及更高版本中的通用 CRT 版本之前的 CRT 尤其如此。 对于使用 Visual Studio 2013 或更低版本生成的 Visual Studio 的每个版本，均有特定于版本的 CRT 库。 CRT 的内部实现详细信息，例如，其数据结构和命名约定，在每个版本中都不同。 为某个版本的 CRT 所编译的代码一直都无法动态链接到不同版本的 CRT DLL，尽管它有时能起作用，但多半是运气使然，而非设计如此。

此外，由于 CRT 库的每个副本都具有自己的堆管理器，因此分配一个 CRT 库中的内存并跨 DLL 边界传递由 CRT 库的不同副本释放的指针可能是导致堆损坏的原因。 如果你设计 DLL 以使其跨边界传递 CRT 对象或分配内存，并期望它可在 DLL 的外部释放，则可仅允许 DLL 应用客户端使用与 DLL 相同的 CRT 库副本。 仅在 DLL 及其客户端都在加载时链接到相同版本的 CRT DLL 时，二者才使用相同的 CRT 库副本。 由于 Windows 10 上的 Visual Studio 2015 和更高版本使用的通用 CRT 库的 DLL 版本现在是一个集中部署的 Windows 组件 ucrtbase.dll，因此它对使用 Visual Studio 2015 及更高版本生成的应用也是一样的。 但是，即使在 CRT 代码完全相同时，你也不能将分配给一个堆的内存移交给使用其他堆的组件。

## <a name="example"></a>示例

### <a name="description"></a>说明

此示例跨 DLL 边界传递文件句柄。

使用 /MD 生成 DLL 和 .exe 文件，二者共享单个 CRT 副本。

如果使用 /MT 重新生成它们以使其使用单独的 CRT 副本，则运行生成的 test1Main.exe 将导致访问冲突。

```cpp
// test1Dll.cpp
// compile with: cl /EHsc /W4 /MD /LD test1Dll.cpp
#include <stdio.h>
__declspec(dllexport) void writeFile(FILE *stream)
{
   char   s[] = "this is a string\n";
   fprintf( stream, "%s", s );
   fclose( stream );
}
```

```cpp
// test1Main.cpp
// compile with: cl /EHsc /W4 /MD test1Main.cpp test1Dll.lib
#include <stdio.h>
#include <process.h>
void writeFile(FILE *stream);

int main(void)
{
   FILE  * stream;
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );
   writeFile(stream);
   system( "type fprintf.out" );
}
```

```Output
this is a string
```

## <a name="example"></a>示例

### <a name="description"></a>说明

此示例跨 DLL 边界传递环境变量。

```cpp
// test2Dll.cpp
// compile with: cl /EHsc /W4 /MT /LD test2Dll.cpp
#include <stdio.h>
#include <stdlib.h>

__declspec(dllexport) void readEnv()
{
   char *libvar;
   size_t libvarsize;

   /* Get the value of the MYLIB environment variable. */
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );

   if( libvar != NULL )
      printf( "New MYLIB variable is: %s\n", libvar);
   else
      printf( "MYLIB has not been set.\n");
   free( libvar );
}
```

```cpp
// test2Main.cpp
// compile with: cl /EHsc /W4 /MT test2Main.cpp test2dll.lib
#include <stdlib.h>
#include <stdio.h>

void readEnv();

int main( void )
{
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );
   readEnv();
}
```

```Output
MYLIB has not been set.
```

如果使用 /MD 同时生成 DLL 和 .exe 文件以便仅使用一个 CRT 副本，则此程序将成功运行并产生以下输出：

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>请参阅

[CRT 库功能](../c-runtime-library/crt-library-features.md)
