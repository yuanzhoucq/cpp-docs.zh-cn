---
title: 常规 MFC 静态链接到 MFC 的 Dll |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c48fdfb0b10541c1643ec49038e29cfa60c633d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383743"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>常规 MFC 静态链接到 MFC 的 Dll
MFC DLL 静态链接到 MFC 正则表达式是在内部，使用 MFC 的 DLL，可以由 MFC 或非 MFC 可执行文件调用 DLL 中导出的函数。 名称所述，使用静态链接库版本的 MFC 进行构建这种类型的 DLL。 函数通常是从正则表达式使用标准的 C 界面的 MFC DLL 导出的。 有关如何编写、 生成和使用的规则的 MFC DLL 的示例，请参见示例[DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。  
  
 请注意，术语 USRDLL 不再使用 Visual c + + 文档中。 静态链接到 MFC 常规 MFC DLL 具有以前的 USRDLL 作为相同的特征。  
  
 常规 MFC DLL 中，静态链接到 MFC，具有以下功能：  
  
-   可以以支持 Dll （C、 c + +、 Pascal、 Visual Basic 等）; 使用任何语言编写的客户端可执行文件它不必是 MFC 应用程序。  
  
-   DLL 可以链接到应用程序使用相同的 MFC 静态链接库。 不再 Dll 的静态链接库的单独版本。  
  
-   在 MFC 4.0 版中之前, USRDLLs 提供相同类型的与静态链接到 MFC 的规则 MFC Dll 的功能。 截至 Visual c + + 版本 4.0 中，术语 USRDLL 已废弃不用。  
  
 常规 MFC DLL 中，静态链接到 MFC，具有以下要求：  
  
-   这种类型的 DLL 必须实例化类派生自`CWinApp`。  
  
-   这种类型的 DLL 将`DllMain`MFC 提供。 所有 DLL 特定初始化将代码都放置在`InitInstance`中的成员函数和终止代码`ExitInstance`如下所示普通的 MFC 应用程序。  
  
-   即使术语 USRDLL 已过时，您仍然必须定义"**_USRDLL**"编译器命令行上。 此定义确定从 MFC 标头文件复制的声明。  
  
 常规 MFC Dll 必须有`CWinApp`-派生的类以及该类应用程序的单个对象一样 MFC 应用程序。 但是，`CWinApp`的 DLL 的对象不具有主消息泵，一样`CWinApp`的应用程序的对象。  
  
 请注意，`CWinApp::Run`机制不适用于 DLL，由于应用程序拥有的主消息泵。 如果 DLL 打开无模式对话框或有其自己的主框架窗口时，应用程序的主消息泵必须调用反过来调用 DLL 导出的例程`CWinApp::PreTranslateMessage`DLL 的应用程序对象的成员函数。  
  
 此函数的示例，请参阅 DLLScreenCap 示例。  
  
 符号通常是从正则表达式使用标准的 C 界面的 MFC DLL 导出的。 从常规 MFC DLL 导出函数的声明将如下所示：  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 常规 MFC DLL 的所有内存分配应都保留在 DLL 中;DLL 不应将传递给或接收从调用的可执行文件的以下任何：  
  
-   指向 MFC 对象的指针  
  
-   对 mfc 分配的内存的指针  
  
 如果你需要进行上述任一操作，或需要调用的可执行文件和 DLL 之间传递 MFC 派生的对象，则必须生成 MFC 扩展 DLL。  
  
 则可以安全地将指针传递给已分配的内存由 C 运行时库应用程序和 DLL 之间仅当你创建的数据副本。 你必须删除或调整这些指针的大小或使用它们而无需制作内存的副本。  
  
 此外可以动态地，静态链接到 MFC 的 DLL 无法链接到共享的 MFC Dll。 静态链接到 MFC 的 DLL 动态绑定到应用程序就像任何其他 DLL;就像任何其他 DLL 中将应用程序链接到它。  
  
 按照中所述的约定命名的标准 MFC 静态链接库[MFC Dll 的命名约定](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)。 但是，使用 MFC 3.0 版及更高版本，它不再需要手动指定到链接器所需中链接的 MFC 库的版本。 MFC 标头文件相反，自动确定要根据预处理器中链接的 MFC 库的正确版本定义，如**\_调试**或 **_UNICODE**。 MFC 标头文件添加 /DEFAULTLIB 指令指示链接器链接 MFC 库的特定版本。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [初始化 MFC 的规则 Dll](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [创建 MFC DLL](../mfc/reference/mfc-dll-wizard.md)  
  
-   [动态链接到 MFC 的规则 MFC DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC 扩展 DLL](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>请参阅  
 [DLL 的类型](../build/kinds-of-dlls.md)