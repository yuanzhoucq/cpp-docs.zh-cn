---
title: 将可执行文件链接到 DLL
ms.date: 08/22/2019
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
ms.openlocfilehash: 0cd9cfa32e6f87479dfcd9926b1735671ff6690f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223936"
---
# <a name="link-an-executable-to-a-dll"></a>将可执行文件链接到 DLL

可执行文件通过以下两种方式之一链接到（或加载）DLL：

- 隐式链接  ，其中操作系统会与使用 DLL 的可执行文件同时加载它。 客户端可执行文件调用 DLL 的导出函数的方式与函数进行静态链接并包含在可执行文件中时的方式相同。 隐式链接有时称为静态加载  或加载时动态链接  。

- 显式链接  ，其中操作系统会在运行时按需加载 DLL。 通过显式链接使用 DLL 的可执行文件必须显式加载和卸载 DLL。 它还必须设置函数指针，用于访问它从 DLL 使用的每个函数。 与静态链接的库或隐式链接 DLL 中的函数调用不同，客户端可执行文件必须通过函数指针调用显式链接 DLL 中的导出函数。 显式链接有时称为动态加载  或运行时动态链接  。

可执行文件可以使用任一链接方法链接到同一个 DLL。 而且，这些方法并不相互排斥；一个可执行文件可以隐式链接到 DLL，另一个可执行文件可以显式附加到它。

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>确定要使用的链接方法

是使用隐式链接还是显式链接是必须为应用程序进行的体系结构决策。 每种方法都各有优缺点。

### <a name="implicit-linking"></a>隐式链接

当应用程序的代码调用导出 DLL 函数时，会进行隐式链接。 当编译或汇编调用可执行文件的源代码时，DLL 函数调用会在对象代码中生成外部函数引用。 若要解析此外部引用，应用程序必须与 DLL 创建者提供的导入库（.lib 文件）链接。

导入库包含的代码仅用于加载 DLL 和实现对 DLL 中函数的调用。 在导入库中查找外部函数会告知链接器该函数的代码处于 DLL 中。 若要解析对 DLL 的外部引用，链接器只需将信息添加到可执行文件，告知系统在进程启动时查找 DLL 代码的位置。

当系统启动包含动态链接引用的程序时，它将使用该程序可执行文件中的信息查找所需 DLL。 如果找不到 DLL，则系统将终止进程，并显示报告错误的对话框。 否则，系统会将 DLL 模块映射到进程地址空间中。

如果任何 DLL 的初始化和终止代码（如 `DllMain`）有入口点函数，则操作系统将调用该函数。 传递给入口点函数的一个参数指定用于指示 DLL 附加到进程的代码。 如果入口点函数不返回 TRUE，则系统将终止进程并报告错误。

最后，系统会修改进程的可执行代码以提供 DLL 函数的起始地址。

与程序代码的其余部分一样，在进程启动时，加载程序会将 DLL 代码映射到进程的地址空间中。 操作系统仅在需要时才将它加载到内存中。 因此，.def 文件在以前 Windows 版本中用于控制加载的 `PRELOAD` 和 `LOADONCALL` 代码特性不再有意义。

### <a name="explicit-linking"></a>显式链接

大多数应用程序使用隐式链接，因为这是可使用的最简单链接方法。 但是，有时需要显式链接。 下面是使用显式链接的一些常见原因：

- 应用程序直到运行时才知道它所加载的 DLL 的名称。 例如，应用程序可能会在启动时从配置文件获取 DLL 的名称和导出函数。

- 如果在使用隐式链接的进程启动时找不到 DLL，则操作系统会终止进程。 使用显式链接的进程在这种情况下不会终止，可以尝试从错误中恢复。 例如，进程可以向用户通知错误，并让用户指定 DLL 的其他路径。

- 如果使用隐式链接的进程所链接到的任何 DLL 的 `DllMain` 函数失败，则进程也会终止。 使用显式链接的进程在这种情况下不会终止。

- 隐式链接到许多 DLL 的应用程序可能会速度较慢，因为 Windows 会在应用程序加载时加载所有 DLL。 若要提高启动性能，应用程序可以只对在加载之后立即需要的 DLL 使用隐式链接。 它可以仅在需要时才使用显式链接加载其他 DLL。

- 显式链接无需使用导入库链接应用程序。 如果 DLL 中的更改导致导出序号发生更改，则在使用函数名称而不是序号值调用 `GetProcAddress` 时，应用程序无需重新链接。 使用隐式链接的应用程序仍必须重新链接到更改的导入库。

下面是需要注意的显式链接方面的两个风险：

- 如果 DLL 具有 `DllMain` 入口点函数，则操作系统会在调用 `LoadLibrary` 的线程的上下文中调用该函数。 如果 DLL 已附加到进程，则不会调用入口点函数，因为以前调用的 `LoadLibrary` 没有对 `FreeLibrary` 函数进行相应调用。 如果 DLL 使用 `DllMain` 函数初始化进程的每个线程，则显式链接可能会导致问题，因为调用 `LoadLibrary`（或 `AfxLoadLibrary`）时已存在的任何线程都不会进行初始化。

- 如果 DLL 将静态范围数据声明为 `__declspec(thread)`，则可能会在进行显式链接时导致保护错误。 在通过调用 `LoadLibrary` 加载 DLL 之后，每当代码引用此数据，便会导致保护错误。 （静态范围数据包含全局和局部静态项。）这就是为什么在创建 DLL 时，应避免使用线程本地存储。 如果不能这样做，请向 DLL 用户告知动态加载 DLL 的潜在陷阱。 有关详细信息，请参阅[在动态链接库中搜索线程本地存储 (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)。

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>如何使用隐式链接

若要通过隐式链接使用 DLL，客户端可执行文件必须从 DLL 的提供程序获取以下文件：

- 一个或多个头文件（.h 文件），其中包含 DLL 中的导出数据、函数和 C++ 类的声明。 DLL 导出的类、函数和数据全都必须在头文件中标记为 `__declspec(dllimport)`。 有关详细信息，请参阅 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。

- 要链接到可执行文件中的导入库。 生成 DLL 时，链接器会创建导入库。 有关详细信息，请参阅 [LIB 文件用作链接器输入](reference/dot-lib-files-as-linker-input.md)。

- 实际 DLL 文件。

若要通过隐式链接使用 DLL 中的数据、函数和类，任何客户端源文件都必须包含声明它们的头文件。 从编码的角度来看，对导出函数的调用与任何其他函数调用一样。

若要生成客户端可执行文件，必须与 DLL 的导入库链接。 如果使用外部生成文件或生成系统，请将导入库与链接的其他对象文件或库一起指定。

当操作系统加载调用可执行文件时，它必须能够找到 DLL 文件。 这意味着必须在安装应用程序时部署 DLL 或验证 DLL 是否存在。

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>如何显式链接到 DLL

若要通过显式链接使用 DLL，应用程序必须在运行时进行函数调用以显式加载 DLL。 若要显式链接到 DLL，应用程序必须：

- 调用 [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) 或类似函数以加载 DLL 并获取模块句柄。

- 调用 [GetProcAddress](getprocaddress.md) 以获取应用程序调用的每个导出函数的函数指针。 由于应用程序通过指针调用 DLL 函数，因此编译器不生成外部引用，从而不需要与导入库链接。 不过，必须有 `typedef` 或 `using` 语句，此语句定义你调用的已导出函数的调用签名。

- 处理完 DLL 时，调用 [FreeLibrary](freelibrary-and-afxfreelibrary.md)。

例如，此示例函数调用 `LoadLibrary` 以加载名为“MyDLL”的 DLL，调用 `GetProcAddress` 以获取指向名为“DLLFunc1”的函数的指针，调用该函数并保存结果，然后调用 `FreeLibrary` 以卸载 DLL。

```C
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)
{
    HINSTANCE hDLL;               // Handle to DLL
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
    HRESULT hrReturnVal;

    hDLL = LoadLibrary("MyDLL");
    if (NULL != hDLL)
    {
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");
        if (NULL != lpfnDllFunc1)
        {
            // call the function
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);
        }
        else
        {
            // report the error
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }
    return hrReturnVal;
}
```

与此示例不同，在大多数情况下，只应在应用程序中对给定 DLL 调用 `LoadLibrary` 和 `FreeLibrary` 一次。 如果要调用 DLL 中的多个函数，或重复调用 DLL 函数，则更是如此。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [使用导入库和导出文件](reference/working-with-import-libraries-and-export-files.md)

- [动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)
