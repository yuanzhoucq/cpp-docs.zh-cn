---
title: "链接到 DLL 的可执行文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6bdc8d4b372a589beb51d2f8a9bc05b1aa241c48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="link-an-executable-to-a-dll"></a>链接到 DLL 的可执行文件  
  
可执行文件链接到 （或加载） DLL 的两种方式之一：  
  
-   *隐式链接*，操作系统使用它的可执行文件加载时从中加载该 DLL。 客户端可执行文件调用 DLL 的导出的函数，就像已以静态方式链接和可执行文件中包含的函数。 隐式链接有时简称为*静态负载*或*负载时动态链接*。  
  
-   *显式链接*、 按需在运行时 DLL 加载操作系统。 使用显式链接的 DLL 的可执行文件必须进行函数调用以显式加载和卸载 DLL，并访问 DLL 导出的函数。 与不同的是对静态链接库中的函数调用中，客户端可执行文件必须通过函数指针的 DLL 中调用导出的函数。 显式链接有时简称为*动态负载*或*运行时动态链接*。  
  
可执行文件可以使用两种链接方法链接到同一个 DLL。 此外，这些方法不是相互排斥;一个可执行文件可以隐式链接到 DLL 并另一个可以显式附加到它。  
  
<a name="determining-which-linking-method-to-use"></a>  
  
## <a name="determine-which-linking-method-to-use"></a>确定要使用的链接方法  
  
你必须使你的应用程序的体系结构决定是否使用隐式链接或通过显式链接。 有一些优点和缺点为每个方法。  
  
### <a name="implicit-linking"></a>隐式链接  
  
当应用程序的代码调用导出的 DLL 函数时发生隐式链接。 当调用的可执行文件的源代码是编译的或汇编时，DLL 函数调用所生成对象代码中的外部函数引用。 若要解决此外部引用，该应用程序必须与链接的 DLL 的创建者提供的导入库 （.lib 文件）。  
  
导入库仅包含代码以加载该 DLL 并在 DLL 中实现对函数的调用。 在导入库中查找一个外部函数，将通知链接器函数的代码是在 DLL 中。 若要解决对 Dll 的外部引用，链接器只需将信息添加到可执行文件，告知在哪里可以找到将 DLL 代码在进程启动时的系统。  
  
系统启动时包含动态链接的引用的程序，它使用信息在程序的可执行文件以查找所需的 Dll。 如果它找不到该 DLL，系统将终止进程，并显示一个对话框，报告此错误。 否则，系统将 DLL 模块映射到进程的地址空间。  
  
如果有任何 Dll 具有初始化和终止代码的入口点函数如`DllMain`，操作系统将调用该函数。 传递给入口点函数的参数之一指定指示 DLL 的代码附加到进程。 如果入口点函数不返回 TRUE，系统将终止进程，并报告错误。  
  
最后，系统将修改为提供的 DLL 函数起始地址的过程的可执行代码。  
  
程序的代码的其余部分，如 DLL 代码映射到进程的地址空间，在进程启动和加载到仅在需要时的内存时。 因此，`PRELOAD`和`LOADONCALL`所使用的.def 文件添加至无法再在以前版本的 Windows 中加载的控制代码特性的含义。  
  
### <a name="explicit-linking"></a>显式链接  
  
大多数应用程序使用隐式链接，因为它是要使用的最简单的方法链接方法。 但是，有的有时也需要显式链接。 下面是一些常见的原因，若要使用显式链接：  
  
-   应用程序不知道它直到运行时加载的 DLL 的名称。 例如，应用程序可能从配置文件在启动时获得该 DLL 导出的函数的名称。  
  
-   使用隐式链接的进程将终止由操作系统在进程启动时找不到 DLL。 使用显式链接的进程未在此情况下终止，并可以尝试从错误中恢复。 例如，进程无法通知错误的用户，让用户指定的 DLL 的另一个路径。  
  
-   使用隐式链接的进程也会被终止，如果有链接具有 Dll`DllMain`失败的函数。 使用显式链接的进程未在此情况下终止。  
  
-   隐式链接到多个 Dll 的应用程序可能较慢启动，因为应用程序加载时，Windows 将加载所有 Dll。 若要提高启动性能，应用程序隐式只能链接到这些其他 Dll 所需显式链接到这些之前立即后加载，并等待所需的 Dll。  
  
-   显式链接无需使用导入库链接应用程序。 如果 DLL 中的更改会导致导出序号以更改，使用显式链接的应用程序不需要重新链接如果它们调用`GetProcAddress`同名的函数并不是一个序号值，而使用隐式链接的应用程序必须重新链接到新的导入库。  
  
下面是显式的链接，需要注意的两个缺点：  
  
-   如果 dll`DllMain`入口点函数，操作系统调用函数调用的线程的上下文中`LoadLibrary`。 如果 DLL 已因以前调用而附加到进程，将不会调用入口点函数`LoadLibrary`已有没有相应地调用`FreeLibrary`函数。 显式链接会导致问题，如果 DLL 使用`DllMain`函数为每个进程的线程中执行初始化，因为线程已存在时`LoadLibrary`(或`AfxLoadLibrary`) 调用未初始化。  
  
-   如果 DLL 声明静态范围数据作为`__declspec(thread)`，如果显式链接，它可能会导致保护错误。 通过调用加载 DLL 后`LoadLibrary`，它会导致保护错误，只要代码引用此数据。 （静态范围数据包括全局和本地静态项。）因此，在创建 DLL 时，应避免使用线程本地存储或提示 DLL 用户有关的动态加载 DLL 的潜在缺陷。 有关详细信息，请参阅[在动态链接库 (Windows SDK) 中使用线程本地存储区](http://msdn.microsoft.com/library/windows/desktop/ms686997)。  
  
<a name="linking-implicitly"></a>  
  
## <a name="how-to-link-implicitly-to-a-dll"></a>如何将隐式链接到 DLL  
  
若要使用通过隐式链接的 DLL，客户端可执行文件必须从该 DLL 的提供程序获取这些文件：  
  
-   一个或多个标头文件 （.h 文件） 包含导出的数据、 函数和/或 DLL 中的 c + + 类的声明。 类、 函数和 DLL 导出的数据必须所有标记`__declspec(dllimport)`标头文件中。 有关详细信息，请参阅[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。  
  
-   导入库链接到可执行文件。 生成 DLL 时，链接器将创建导入库。 有关详细信息，请参阅[。LIB 文件](../build/reference/dot-lib-files-as-linker-input.md)。  
  
-   实际的 DLL 文件。  
  
若要使用通过隐式链接的 DLL，可执行文件必须包括数据、 函数或包含对导出的数据、 函数和类的调用每个源文件中 DLL 导出的 c + + 类声明的头文件。 从编码的角度来看，对导出的函数的调用是就像任何其他函数调用一样。  
  
若要生成的调用的可执行文件，必须与导入库链接。 如果你使用外部生成文件，或生成系统，指定在其中列出其他对象 (.obj) 文件的导入库或你将链接的库的文件名称。  
  
操作系统必须能够找到 DLL 文件加载调用的可执行文件时。 这意味着你的应用程序必须部署或安装你的应用程序时验证 DLL 存在。   
  
<a name="linking-explicitly"></a>  
  
## <a name="how-to-link-explicitly-to-a-dll"></a>如何显式链接到 DLL  
  
若要使用由显式链接的 DLL，应用程序必须进行函数调用以在运行时显式加载 DLL。 若要显式链接到 DLL，应用程序必须：  
  
-   调用[LoadLibrary](loadlibrary-and-afxloadlibrary.md)， `LoadLibraryEx`，或类似函数加载的 DLL，并获取模块句柄。  
  
-   调用[GetProcAddress](getprocaddress.md)获取函数指针到每个导出的应用程序调用的函数。 应用程序调用 DLL 函数通过指针，因为编译器不生成外部引用，因此无需与导入的库链接。 但是，你必须具有`typedef`或`using`定义导出函数调用的调用签名的语句。   
  
-   调用[FreeLibrary](freelibrary-and-afxfreelibrary.md)完成 DLL。  
  
例如，此示例函数将调用`LoadLibrary`加载名为"MyDLL"DLL 调用`GetProcAddress`若要获取指向一个名为"DLLFunc1"函数的调用函数并保存结果，然后调用`FreeLibrary`卸载 DLL。 
  
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
  
与不同在此示例中，在大多数情况下应调用`LoadLibrary`和`FreeLibrary`唯一一次是在你的应用程序对于给定的 DLL，尤其是如果你要在 DLL 中调用多个函数或调用 DLL 函数重复。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [使用导入库和导出文件](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Windows 用来定位 DLL 搜索路径](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)