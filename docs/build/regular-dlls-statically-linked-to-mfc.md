---
title: "静态链接到 MFC 的规则 DLL | Microsoft Docs"
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
  - "DLL [C++], 规则"
  - "规则 DLL [C++]"
  - "规则 DLL [C++], 静态链接到 MFC"
  - "静态链接的 DLL [C++]"
  - "USRDLL"
  - "USRDLL, 静态链接到 MFC"
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 静态链接到 MFC 的规则 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

静态链接到 MFC 的规则 DLL 是在内部使用 MFC 的 DLL，这类 DLL 中的导出函数可由 MFC 或非 MFC 可执行文件调用。  正如名称所描述的，这类 DLL 是使用 MFC 静态链接库版本生成的。  函数通常是通过标准 C 接口从规则 DLL 导出的。  有关如何编写、生成和使用规则 DLL 的示例，请参见示例 [DLLScreenCap](http://msdn.microsoft.com/zh-cn/2171291d-3a50-403b-90a1-d93c2acb4f4a)。  
  
 请注意，Visual C\+\+ 文档中不再使用 USRDLL 一词。  静态链接到 MFC 的规则 DLL 具有与原来的 USRDLL 相同的特性。  
  
 静态链接到 MFC 的规则 DLL 具有下列功能：  
  
-   客户端可执行文件可以用任何支持使用 DLL 的语言（C、C\+\+、Pascal、Visual Basic 等）编写；它不必是 MFC 应用程序。  
  
-   DLL 可以链接到由应用程序使用的同一 MFC 静态链接库。  已不再有单独用于 DLL 的静态链接库版本。  
  
-   在 MFC 4.0 版之前，USRDLL 与静态链接到 MFC 的规则 DLL 提供相同的功能类型。  自 Visual C\+\+ 4.0 版起，“USRDLL”一词已过时。  
  
 静态链接到 MFC 的规则 DLL 具有下列要求：  
  
-   这类 DLL 必须实例化从 `CWinApp` 派生的类。  
  
-   此类型的 DLL 使用 MFC 提供的 `DllMain`。  与在标准 MFC 应用程序中一样，将所有 DLL 特定的初始化代码放到 `InitInstance` 成员函数中，将终止代码放到 `ExitInstance` 中。  
  
-   尽管“USRDLL”一词已过时，但仍必须在编译器命令行上定义“**\_USRDLL**”。  此定义确定从 MFC 头文件中复制的声明。  
  
 与 MFC 应用程序相同，规则 DLL 必须有一个 `CWinApp` 派生的类和此应用程序类的单个对象。  然而，与应用程序的 `CWinApp` 对象不同，DLL 的 `CWinApp` 对象没有主消息泵。  
  
 请注意，`CWinApp::Run` 机制不适用于 DLL，因为应用程序拥有主消息泵。  如果 DLL 打开无模式对话框或有自己的主框架窗口，则应用程序的主消息泵必须调用由 DLL 导出的例程，而该例程应会反过来调用 DLL 应用程序对象的 `CWinApp::PreTranslateMessage` 成员函数。  
  
 有关此函数的示例，请参见 DLLScreenCap 示例。  
  
 符号通常是通过标准 C 接口从规则 DLL 导出的。  从规则 DLL 导出的函数的声明形如：  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 规则 DLL 内的所有内存分配都应在该 DLL 内进行；DLL 不应向调用可执行文件传递或从调用可执行文件接收下列任何指针：  
  
-   指向 MFC 对象的指针  
  
-   指向由 MFC 分配的内存的指针  
  
 如果需要执行上述任一操作，或者需要在调用可执行文件和 DLL 之间传递 MFC 派生的对象，则必须生成扩展 DLL。  
  
 仅当创建了数据副本后，在应用程序和 DLL 之间传递指向 C 运行库所分配的内存的指针才是安全的。  一定不要删除这些指针或调整它们的大小，也不要在没有创建内存副本的情况下使用这些指针。  
  
 静态链接到 MFC 的 DLL 无法同时动态链接到共享 MFC DLL。  静态链接到 MFC 的 DLL 像任何其他 DLL 一样动态绑定到应用程序；而应用程序像任何其他 DLL 一样链接到静态链接到 MFC 的 DLL。  
  
 标准 MFC 静态链接库依据 [MFC DLL 命名约定](../build/naming-conventions-for-mfc-dlls.md)中描述的约定进行命名。  但是，在 MFC 3.0 版及更高版本中，不再需要向链接器手动指定希望链接的 MFC 库版本，  而是由 MFC 头文件基于预处理器定义（如 **\_DEBUG** 或 **\_UNICODE**）自动确定要链接到的 MFC 库的正确版本。  MFC 头文件添加 \/DEFAULTLIB 指令来指示链接器链接到特定的 MFC 库版本中。  
  
## 你希望做什么？  
  
-   [初始化规则 DLL](../build/initializing-regular-dlls.md)  
  
## 您想进一步了解什么？  
  
-   [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [在规则 DLL 中使用数据库、OLE 和套接字扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [创建 MFC DLL](../mfc/reference/mfc-dll-wizard.md)  
  
-   [动态链接到 MFC 的规则 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [扩展 DLL](../build/extension-dlls-overview.md)  
  
## 请参阅  
 [DLL 类型](../build/kinds-of-dlls.md)