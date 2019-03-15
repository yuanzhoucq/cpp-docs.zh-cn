---
title: 链接到 DLL 的可执行文件
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
ms.openlocfilehash: fc7a676059af17e7a42189c7c15ca157a081e08a
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "57818357"
---
# <a name="link-an-executable-to-a-dll"></a>链接到 DLL 的可执行文件

可执行文件链接到 （或加载） DLL 中有两种：

- *隐式链接*，其中操作系统加载该 DLL 加载时使用它的可执行文件。 客户端可执行文件调用 DLL 的导出的函数，就像是以静态方式链接和可执行文件中包含的函数。 隐式链接有时称为*静态负载*或*加载时动态链接*。

- *显式链接*、 按需在运行时 DLL 加载操作系统。 通过显式链接中使用的 DLL 的可执行文件必须进行函数调用以显式加载和卸载该 DLL，并访问 DLL 导出的函数。 与不同的是对静态链接库中的函数调用中，客户端可执行文件必须通过函数指针的 DLL 中调用导出的函数。 显式链接有时称为*动态负载*或*运行时动态链接*。

可执行文件可以使用两种链接方法链接到同一个 DLL。 此外，这些方法不是相互排斥;一个可执行文件可以隐式链接到 DLL 和另一个可显式附加到它。

<a name="determining-which-linking-method-to-use"></a>

## <a name="link-an-executable-to-a-dll"></a>链接到 DLL 的可执行文件

是使用隐式链接还是显式链接是一个必须进行应用程序的体系结构决策。 有一些优点和缺点的每个方法。

### <a name="implicit-linking"></a>隐式链接

应用程序的代码将调用一个导出的 DLL 函数时发生隐式链接。 时调用的可执行文件的源代码是编译的或汇编，DLL 函数调用中的对象代码生成的外部函数引用。 若要解决此外部引用，该应用程序必须使用链接的 DLL 的创建者所提供的导入库 （.lib 文件）。

导入库仅包含代码来加载的 DLL 以及 DLL 中实现对函数的调用。 导入库中查找一个外部函数通知链接器，该函数的代码是在 DLL 中。 若要解决对 Dll 的外部引用，链接器只需将信息添加到指示系统在哪里可以找到 DLL 代码时在进程启动的可执行文件。

系统启动时包含动态链接的引用的程序，它使用信息在程序的可执行文件中查找所需的 Dll。 如果找不到该 DLL，系统将终止进程，并显示一个对话框，报告该错误。 否则，系统将 DLL 模块映射到进程的地址空间。

如果的任何 Dll 具有入口点函数的初始化和终止代码如`DllMain`，操作系统将调用该函数。 传递给入口点函数的参数之一指定指示 DLL 的代码附加到进程。 如果入口点函数不返回 TRUE，系统将终止进程，并报告错误。

最后，系统将修改要提供起始地址的 DLL 函数的进程的可执行代码。

程序的代码的其余部分，如 DLL 代码映射到进程的地址空间，在进程启动并加载到仅在需要时的内存时。 因此，`PRELOAD`和`LOADONCALL`使用.def 文件添加至控制不能再在以前版本的 Windows 中加载的代码特性的含义。

### <a name="explicit-linking"></a>显式链接

大多数应用程序使用隐式链接，因为它是最易于链接方法使用。 但是，有些的时候也需要显式链接。 下面是一些常见的原因，若要使用显式链接：

- 应用程序不知道它直到运行时加载的 DLL 的名称。 例如，应用程序可以从配置文件在启动时获取该 DLL 导出的函数的名称。

- 使用隐式链接的进程将终止由操作系统在进程启动时找不到 DLL。 使用显式链接的进程未在此情况下终止，并可以尝试从错误中恢复。 例如，进程无法通知错误的用户，并让用户指定另一个 DLL 路径。

- 如果有链接具有的 Dll，则也会终止使用隐式链接的进程`DllMain`失败的函数。 使用显式链接的进程未在此情况下终止。

- 隐式链接到许多 Dll 的应用程序可能较慢，若要启动，因为应用程序加载时，Windows 将加载所有 Dll。 若要提高启动性能，应用程序隐式只能链接到这些 Dll 后需要立即加载，并等待，直到其他 Dll 所需显式链接到它们。

- 显式链接不再需要使用导入库链接应用程序。 如果 DLL 中的更改会导致导出序号，若要更改，使用显式链接的应用程序不需要重新链接它们调用`GetProcAddress`使用的名称以及一个函数不是一个序号值，而使用隐式链接的应用程序必须重新链接到新的导入库。

下面是需要注意的显式链接的两个缺点：

- 如果 DLL 具有`DllMain`入口点函数，操作系统将调用的线程中调用的上下文中该函数`LoadLibrary`。 如果 DLL 已附加到进程由于以前调用，将不会调用入口点函数`LoadLibrary`已有没有相应地调用`FreeLibrary`函数。 显式链接可能导致问题，如果 DLL 使用`DllMain`函数来执行的进程的每个线程初始化，因为线程已存在时`LoadLibrary`(或`AfxLoadLibrary`) 称为未初始化。

- 如果 DLL 声明静态作用域数据作为`__declspec(thread)`，如果显式链接，它可能会导致保护错误。 通过调用加载 DLL 后`LoadLibrary`，它会导致保护错误，只要代码引用此数据。 （静态作用域数据包括全局和局部静态项。）因此，当您创建 DLL，您应避免使用线程本地存储或提示 DLL 用户有关的动态加载 DLL 的隐患。 有关详细信息，请参阅[在动态链接库 (Windows SDK) 中使用线程本地存储区](/windows/desktop/Dlls/using-thread-local-storage-in-a-dynamic-link-library)。

<a name="linking-implicitly"></a>

## <a name="link-an-executable-to-a-dll"></a>链接到 DLL 的可执行文件

若要使用的隐式链接的 DLL，客户端的可执行文件必须从该 DLL 的提供程序获得这些文件：

- 一个或多个标头文件 （.h 文件），包含导出的数据、 函数和/或 DLL 中的 c + + 类的声明。 类、 函数和 DLL 导出的数据必须所有标记为`__declspec(dllimport)`标头文件中。 有关详细信息，请参阅[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。

- 导入库链接到可执行文件。 生成 DLL 时，链接器创建的导入库。 有关详细信息，请参阅[。LIB 文件](reference/dot-lib-files-as-linker-input.md)。

- 实际的 DLL 文件。

若要使用通过隐式链接的 DLL，可执行文件必须包含声明的数据、 函数或 c + + 类中每个源文件，其中包含对导出的数据、 函数和类的调用 DLL 导出的标头文件。 从编码的角度来看，对导出的函数调用是就像任何其他函数调用一样。

若要生成的调用的可执行文件，必须使用导入库链接。 如果使用外部生成文件或生成系统时，指定在其中列出的其他对象 (.obj) 文件的导入库或链接的库的文件名称。

操作系统必须能够找到 DLL 文件加载调用可执行文件时。 这意味着你的应用程序必须部署或安装应用程序时验证 DLL 存在。

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>如何显式链接到 DLL

若要使用的显式链接的 DLL，应用程序必须进行函数调用以在运行时显式加载该 DLL。 若要显式链接到 DLL，应用程序必须：

- 调用[LoadLibrary](loadlibrary-and-afxloadlibrary.md)， `LoadLibraryEx`，或类似的功能，若要加载的 DLL，并获取模块句柄。

- 调用[GetProcAddress](getprocaddress.md)获取函数指针到每个导出的应用程序调用的函数。 应用程序调用 DLL 函数通过指针，因为编译器不生成外部引用，因此无需使用导入库链接。 但是，您必须具有`typedef`或`using`调用导出函数的调用签名定义的语句。

- 调用[FreeLibrary](freelibrary-and-afxfreelibrary.md)完成 DLL。

例如，此示例函数将调用`LoadLibrary`加载名为"MyDLL"的 DLL 调用`GetProcAddress`若要获取指向名为"DLLFunc1"的函数的调用函数并将结果，保存，然后调用`FreeLibrary`卸载该 DLL。

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

不同于在此示例中，在大多数情况下应调用`LoadLibrary`和`FreeLibrary`仅一次是在你的应用程序对于给定的 DLL，尤其是要在 DLL 中调用多个函数或调用 DLL 函数重复。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [使用导入库和导出文件](reference/working-with-import-libraries-and-export-files.md)

- [动态链接库搜索顺序](/windows/desktop/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](dlls-in-visual-cpp.md)
