---
title: 了解 Visual c + + 应用程序的依赖关系 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application deployment [C++], dependencies
- Dependency Walker
- dependencies [C++], application deployment and
- deploying applications [C++], dependencies
- DUMPBIN utility
- DLLs [C++], dependencies
- depends.exe
- libraries [C++], application deployment issues
ms.assetid: 62a44c95-c389-4c5f-82fd-07d7ef09dbf9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da2aadeba69a8be29627650ba6ef24516098a8e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>了解 Visual C++ 应用程序的依赖项
若要确定取决于应用程序的 Visual c + + 库，你可以查看项目属性。 (在解决方案资源管理器，右键单击该项目并选择**属性**以打开**属性页**对话框。)你还可以使用 Dependency Walker (depends.exe)，以更全面地了解依赖项。  
  
 在**属性页**对话框中，你可以检查下的各个页面**配置属性**要了解依赖项。 例如，如果你的项目使用 MFC 库并且你选择**MFC 的使用**，**在共享的 DLL 中使用 MFC**上**配置属性**，**常规**页上，应用程序在运行时依赖于 MFC Dll 如 mfc\<版本 >.dll。 如果你的应用程序不使用 MFC，它可能依赖于 CRT 库如果你选择**运行时库**值**多线程调试 DLL (/ MDd)** 或**多线程 DLL (/ MD)** 上**配置属性**， **C/c + +**，**代码生成**页。  
  
 确定应用程序依赖哪些 DLL 的更全面的方式是：使用 Dependency Walker (depends.exe) 打开该应用程序。 你可以下载中的工具[Dependency Walker](http://go.microsoft.com/fwlink/p/?LinkId=132640) web 站点。  
  
 通过使用 depends.exe，可以检查在加载时链接到应用程序的 DLL 的列表及延迟加载的 DLL 的列表。 如果要获取在运行时动态加载的 DLL 的完整列表，可在 depends.exe 中使用分析功能来测试应用程序，直到你确定所有代码路径都已执行过。 在结束分析会话时，depends.exe 将显示在运行时动态加载了哪些 DLL。  
  
 使用 depends.exe 时，请注意，一个 DLL 可能依赖于另一个 DLL 或特定版本的 DLL。 可以在开发计算机上或目标计算机上使用 Depends.exe。 在开发计算机上，Depends.exe 将报告支持应用程序所需要的 DLL。 如果在目标计算机上运行应用程序时遇到问题，可以将 depends.exe 复制到计算机上，然后在该工具中打开应用程序，以便确定是否有任何必要的 DLL 丢失或不正确。  
  
 在你知道应用程序所依赖的 DLL 后，就可以在将应用程序部署到另一个计算机时确定哪些 DLL 必须与其一起重新发布。 在大多数情况下，无需重新发布系统 Dll，但你可能需要将 Dll 重新分发 Visual c + + 库。 有关详细信息，请参阅[确定要重新分发的 Dll](../ide/determining-which-dlls-to-redistribute.md)。  
  
## <a name="see-also"></a>请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)