---
title: 将可执行文件链接到 DLL
ms.date: 11/04/2016
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
ms.openlocfilehash: c4f9ea7a3606612189e85401b75a0577896fd90e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493228"
---
# <a name="link-an-executable-to-a-dll"></a>将可执行文件链接到 DLL

可执行文件通过以下两种方式之一链接到 (或加载) DLL:

- *隐式链接*, 其中, 当加载 DLL 时, 操作系统将加载 DLL。 客户端可执行文件调用 DLL 的导出函数, 就像函数是静态链接的并且包含在可执行文件中一样。 隐式链接有时称为*静态负载*或*加载时动态链接*。

- *显式链接*, 其中操作系统在运行时按需加载 DLL。 通过显式链接使用 DLL 的可执行文件必须进行函数调用以显式加载和卸载 DLL, 以及访问由 DLL 导出的函数。 与对静态链接库中的函数的调用不同, 客户端可执行文件必须通过函数指针调用 DLL 中的导出函数。 显式链接有时称为*动态加载*或*运行时动态链接*。

可执行文件可以使用链接方法链接到同一个 DLL。 此外, 这些方法并不相互排斥;一个可执行文件可以隐式链接到 DLL, 另一个可执行文件显式附加到 DLL。

<a name="determining-which-linking-method-to-use"></a>

## <a name="link-an-executable-to-a-dll"></a>将可执行文件链接到 DLL

是使用隐式链接还是显式链接是您必须为您的应用程序制定的体系结构决策。 每种方法都有优缺点。

### <a name="implicit-linking"></a>隐式链接

当应用程序的代码调用导出的 DLL 函数时, 将发生隐式链接。 当编译或汇编调用可执行文件的源代码时, DLL 函数调用会在对象代码中生成外部函数引用。 若要解析此外部引用, 应用程序必须与 DLL maker 提供的导入库 (.lib 文件) 链接。

导入库只包含用于加载 DLL 和实现对 DLL 中函数的调用的代码。 在导入库中查找外部函数会通知链接器该函数的代码位于一个 DLL 中。 为了解析对 Dll 的外部引用, 链接器只是将信息添加到可执行文件, 该文件告诉系统在进程启动时查找 DLL 代码的位置。

当系统启动包含动态链接引用的程序时, 它将使用该程序的可执行文件中的信息来查找所需的 Dll。 如果找不到 DLL, 系统将终止进程, 并显示一个报告错误的对话框。 否则, 系统会将 DLL 模块映射到进程的地址空间。

如果任何 dll 具有用于初始化和终止代码 (如`DllMain`) 的入口点函数, 则操作系统将调用函数。 传递给入口点函数的一个参数指定一个代码, 用于指示 DLL 附加到进程。 如果入口点函数不返回 TRUE, 则系统将终止进程并报告错误。

最后, 系统修改进程的可执行代码以提供 DLL 函数的起始地址。

与程序代码的其余部分一样, DLL 代码在进程启动时映射到进程的地址空间中, 并且仅在需要时才加载到内存中。 因此, 在以前版本`PRELOAD`的`LOADONCALL` Windows 中, 用于控制加载的 .def 文件使用的和代码属性不再有意义。

### <a name="explicit-linking"></a>显式链接

大多数应用程序使用隐式链接, 因为它是最简单的链接方法。 但是, 有时需要显式链接。 下面是使用显式链接的一些常见原因:

- 应用程序不知道它在运行时所加载的 DLL 的名称。 例如, 应用程序可能会在启动时从配置文件中获取 DLL 的名称和导出的函数。

- 如果在进程启动时找不到 DLL, 则操作系统终止使用隐式链接的进程。 在这种情况下, 使用显式链接的进程不会终止, 并可能尝试从错误中恢复。 例如, 进程可能会向用户通知错误, 并让用户指定 DLL 的其他路径。

- 如果要链接到的任何 dll 具有`DllMain`失败的函数, 则使用隐式链接的进程也会终止。 在这种情况下, 使用显式链接的进程不会终止。

- 隐式链接到多个 Dll 的应用程序可能会很慢, 因为在应用程序加载时, Windows 会加载所有 Dll。 若要提高启动性能, 应用程序可以隐式地链接到那些在加载后立即需要的 Dll, 并等待其他 Dll 显式链接到它们。

- 显式链接无需通过使用导入库来链接应用程序。 如果 DLL 中的更改导致导出序号更改, 则使用显式链接的应用程序在使用函数名称而不是序号`GetProcAddress`值调用时无需重新链接, 而使用隐式链接的应用程序必须重新链接到新导入库。

下面是显式链接需要注意的两个风险:

- 如果 DLL 具有`DllMain`入口点函数, 则操作系统会在调用`LoadLibrary`的线程的上下文中调用函数。 如果 DLL 已附加到进程, 则不会调用入口点函数, 因为对`LoadLibrary`的前一次调用没有相应的`FreeLibrary`函数调用。 如果 DLL 使用`DllMain`函数为进程的每个线程执行初始化, 则显式链接会导致出现问题, 因为调用 (或`AfxLoadLibrary`) `LoadLibrary`时已存在的线程未初始化。

- 如果 DLL 将静态范围数据声明为`__declspec(thread)`, 则可能会在显式链接时导致保护错误。 在通过调用`LoadLibrary`加载 DLL 后, 只要代码引用此数据, 就会导致保护错误。 (静态范围数据同时包含全局和局部静态项。)因此, 创建 DLL 时, 应避免使用线程本地存储或通知 DLL 用户有关动态加载 DLL 的潜在陷阱。 有关详细信息, 请参阅[在动态链接库中使用线程本地存储 (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)。

<a name="linking-implicitly"></a>

## <a name="link-an-executable-to-a-dll"></a>将可执行文件链接到 DLL

若要通过隐式链接使用 DLL, 客户端可执行文件必须从 DLL 的提供程序获取以下文件:

- 一个或多个标头文件 (.h 文件), 其中包含 DLL 中导出的数据、函数和/ C++或类的声明。 DLL 导出的类、函数和数据必须全部标记`__declspec(dllimport)`在标头文件中。 有关详细信息，请参阅 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。

- 要链接到可执行文件的导入库。 生成 DLL 时, 链接器将创建导入库。 有关详细信息, 请参阅[。LIB 文件](reference/dot-lib-files-as-linker-input.md)。

- 实际的 DLL 文件。

若要通过隐式链接使用 DLL, 可执行文件必须包含用于声明数据的头文件、包含C++对已导出数据、函数和类的调用的每个源文件中由 DLL 导出的函数或类。 从编码的角度来看, 对导出的函数的调用与任何其他函数调用一样。

若要生成调用可执行文件, 必须链接到导入库。 如果使用外部生成文件或生成系统, 请指定导入库的文件名, 你将在其中列出你链接的其他对象 (.obj) 文件或库。

当操作系统加载调用可执行文件时, 它必须能够找到 DLL 文件。 这意味着, 在安装应用程序时, 应用程序必须部署或验证 DLL 是否存在。

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>如何显式链接到 DLL

若要通过显式链接使用 DLL, 应用程序必须在运行时进行函数调用以显式加载 DLL。 若要显式链接到 DLL, 应用程序必须:

- 调用[LoadLibrary](loadlibrary-and-afxloadlibrary.md)、 `LoadLibraryEx`或类似的函数来加载 DLL 并获取模块句柄。

- 调用[GetProcAddress](getprocaddress.md)以获取应用程序调用的每个导出函数的函数指针。 由于应用程序通过指针调用 DLL 函数, 因此编译器不生成外部引用, 因此不需要与导入库链接。 但是, 您必须有一个`typedef`或`using`语句来定义您调用的导出函数的调用签名。

- 完成 DLL 后, 调用[FreeLibrary](freelibrary-and-afxfreelibrary.md) 。

例如, 此示例函数调用`LoadLibrary`以加载一个名为 "MyDLL" 的 DLL, 调用`GetProcAddress`以获取指向名为 "DLLFunc1" 的函数的指针, 调用该函数并保存结果, 然后调用`FreeLibrary`来卸载该 dll。

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

与在此示例中不同, 在大多数情况下`LoadLibrary` , `FreeLibrary`你应在应用程序中为给定的 DLL 调用且仅一次, 尤其当你要重复调用 dll 中的多个函数或重复调用 dll 函数时。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [使用导入库和导出文件](reference/working-with-import-libraries-and-export-files.md)

- [动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)
