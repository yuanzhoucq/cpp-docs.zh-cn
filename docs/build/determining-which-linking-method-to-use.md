---
title: "确定要使用的链接方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "显式链接 [C++]"
  - "隐式链接 [C++]"
ms.assetid: 6b6d3fec-4711-4a30-af5b-354b965ecaec
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 确定要使用的链接方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有两种类型的链接：隐式链接和显式链接。  
  
## 隐式链接  
 应用程序的代码调用导出 DLL 函数时发生[隐式链接](../build/linking-implicitly.md)。  当调用可执行文件的源代码被编译或被汇编时，DLL 函数调用在对象代码中生成一个外部函数引用。  若要解析此外部引用，应用程序必须与 DLL 的创建者所提供的导入库（.LIB 文件）链接。  
  
 导入库仅包含加载 DLL 的代码和实现 DLL 函数调用的代码。  在导入库中找到外部函数后，会通知链接器此函数的代码在 DLL 中。  要解析对 DLL 的外部引用，链接器只需向可执行文件中添加信息，通知系统在进程启动时应在何处查找 DLL 代码。  
  
 系统启动包含动态链接引用的程序时，它使用程序的可执行文件中的信息定位所需的 DLL。  如果系统无法定位 DLL，它将终止进程并显示一个对话框来报告错误。  否则，系统将 DLL 模块映射到进程的地址空间中。  
  
 如果任何 DLL 具有（用于初始化代码和终止代码的）入口点函数，操作系统将调用此函数。  在传递到入口点函数的参数中，有一个指定用以指示 DLL 正在附带到进程的代码。  如果入口点函数没有返回 TRUE，系统将终止进程并报告错误。  
  
 最后，系统修改进程的可执行代码以提供 DLL 函数的起始地址。  
  
 与程序代码的其余部分一样，DLL 代码在进程启动时映射到进程的地址空间中，且仅当需要时才加载到内存中。  因此，由 .def 文件用来在 Windows 的早期版本中控制加载的 **PRELOAD** 和 **LOADONCALL** 代码特性不再具有任何意义。  
  
## 显式链接  
 大部分应用程序使用隐式链接，因为这是最易于使用的链接方法。  但是有时也需要[显式链接](../build/linking-explicitly.md)。  下面是一些使用显式链接的常见原因：  
  
-   直到运行时，应用程序才知道需要加载的 DLL 的名称。  例如，应用程序可能需要从配置文件获取 DLL 的名称和导出函数名。  
  
-   如果在进程启动时未找到 DLL，操作系统将终止使用隐式链接的进程。  同样是在此情况下，使用显式链接的进程则不会被终止，并可以尝试从错误中恢复。  例如，进程可通知用户所发生的错误，并让用户指定 DLL 的其他路径。  
  
-   如果使用隐式链接的进程所链接到的 DLL 中有任何 DLL 具有失败的 `DllMain` 函数，该进程也会被终止。  同样是在此情况下，使用显式链接的进程则不会被终止。  
  
-   因为 Windows 在应用程序加载时加载所有的 DLL，故隐式链接到许多 DLL 的应用程序启动起来会比较慢。  为提高启动性能，应用程序可隐式链接到那些加载后立即需要的 DLL，并等到在需要时显式链接到其他 DLL。  
  
-   显式链接下不需将应用程序与导入库链接。  如果 DLL 中的更改导致导出序号更改，使用显式链接的应用程序不需重新链接（假设它们是用函数名而不是序号值调用 **GetProcAddress**），而使用隐式链接的应用程序必须重新链接到新的导入库。  
  
 下面是需要注意的显式链接的两个缺点：  
  
-   如果 DLL 具有 `DllMain` 入口点函数，则操作系统在调用 **LoadLibrary** 的线程上下文中调用此函数。  如果由于以前调用了 **LoadLibrary** 但没有相应地调用 **FreeLibrary** 函数而导致 DLL 已经附加到进程，则不会调用此入口点函数。  如果 DLL 使用 `DllMain` 函数为进程的每个线程执行初始化，显式链接会造成问题，因为调用 **LoadLibrary**（或 `AfxLoadLibrary`）时存在的线程将不会初始化。  
  
-   如果 DLL 将静态作用域数据声明为 **\_\_declspec\(thread\)**，则在显式链接时 DLL 会导致保护错误。  用 **LoadLibrary** 加载 DLL 后，每当代码引用此数据时 DLL 就会导致保护错误。（静态作用域数据既包括全局静态项，也包括局部静态项。）因此，创建 DLL 时应避免使用线程本地存储区，或者应（在用户尝试动态加载时）告诉 DLL 用户潜在的缺陷。  
  
## 你希望做什么？  
  
-   [隐式链接](../build/linking-implicitly.md)  
  
-   [显式链接](../build/linking-explicitly.md)  
  
## 您想进一步了解什么？  
  
-   [Windows 用来定位 DLL 的搜索路径](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
-   [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [\<caps:sentence id\="tgt47" sentenceid\="8081a197f9413cac12a30b57c2612af5" class\="tgtSentence"\>在动态链接库中使用线程本地存储区 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms686997)  
  
## 请参阅  
 [将可执行文件链接到 DLL](../build/linking-an-executable-to-a-dll.md)