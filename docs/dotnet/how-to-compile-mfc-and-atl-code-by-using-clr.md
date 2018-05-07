---
title: 如何： 通过使用 clr 编译 MFC 和 ATL 代码 |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], interoperability
- ATL [C++], interoperability
- mixed assemblies [C++], MFC code
- mixed assemblies [C++], ATL code
- /clr compiler option [C++], compiling ATL and MFC code
- interoperability [C++], /clr compiler option
- regular MFC DLLs [C++], /clr compiler option
- interop [C++], /clr compiler option
- extension DLLs [C++], /clr compiler option
ms.assetid: 12464bec-33a4-482c-880a-c078de7f6ea5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7412d69230bcb6375a042d6cf8e8f27a3d9eac9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>如何：使用 /clr 编译 MFC 和 ATL 代码
本主题讨论如何将现有的 MFC 和 ATL 程序，以面向公共语言运行时编译。  
  
### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>若要通过使用 /clr 编译 MFC 可执行文件或正则 MFC DLL  
  
1.  右键单击中的项目**解决方案资源管理器**，然后单击**属性**。  
  
2.  在**项目属性**对话框框中，展开的节点旁边**配置属性**和选择**常规**。 在右窗格中，在**项目默认值**，将其设置**公共语言运行时支持**到**公共语言运行时支持 (/ clr)**。  
  
     在同一窗格中，请确保**MFC 的使用**设置为**在共享的 DLL 中使用 MFC**。  
  
3.  下**配置属性**，展开的节点旁边**C/c + +** 和选择**常规**。 请确保**调试信息格式**设置为**程序数据库 /Zi** (不 **/ZI**)。  
  
4.  选择**代码生成**节点。 设置**启用最小重新生成**到**否 (/ Gm-)**。 此外设置**基本运行时检查**到**默认**。  
  
5.  下**配置属性**，选择**C/c + +** 然后**代码生成**。 请确保**运行时库**设置为**多线程调试 DLL (/ MDd)** 或**多线程 DLL (/ MD)**。  
  
6.  在 stdafx.h 文件中，添加以下行。  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>若要通过使用 /clr 编译 MFC 扩展 DLL  
  
1.  按照"若要编译 MFC 可执行文件或正则 MFC DLL 使用 /clr"中的步骤。  
  
2.  下**配置属性**，展开的节点旁边**C/c + +** 和选择**预编译标头**。 设置**创建/使用预编译标头**到**不使用预编译标头**。  
  
     作为替代方法，在**解决方案资源管理器**，右键单击 Stdafx.cpp，然后单击**属性**。 下**配置属性**，展开的节点旁边**C/c + +** 和选择**常规**。 设置**具有公共语言运行时支持的编译**到**无公共语言运行库支持**。  
  
3.  对于包含 DllMain 和任何内容的文件，它调用，在**解决方案资源管理器**，右键单击该文件，然后单击**属性**。 下**配置属性**，展开的节点旁边**C/c + +** 和选择**常规**。 在右窗格中，在**项目默认值**，将其设置**具有公共语言运行时支持的编译**到**无公共语言运行库支持**。  
  
### <a name="to-compile-an-atl-executable-by-using-clr"></a>若要通过使用 /clr 编译的 ATL 可执行文件  
  
1.  在**解决方案资源管理器**，右键单击项目，然后单击**属性**。  
  
2.  在**项目属性**对话框框中，展开的节点旁边**配置属性**和选择**常规**。 在右窗格中，在**项目默认值**，将其设置**公共语言运行时支持**到**公共语言运行时支持 (/ clr)**。  
  
3.  下**配置属性**，展开的节点旁边**C/c + +** 和选择**常规**。 请确保**调试信息格式**设置为**程序数据库 /Zi** (不 **/ZI**)。  
  
4.  选择**代码生成**节点。 设置**启用最小重新生成**到**否 (/ Gm-)**。 此外设置**基本运行时检查**到**默认**。  
  
5.  下**配置属性**，选择**C/c + +** 然后**代码生成**。 请确保**运行时库**设置为**多线程调试 DLL (/ MDd)** 或**多线程 DLL (/ MD)**。  
  
6.  对于 MIDL 生成的每个文件 （C 文件），请右键单击中的文件**解决方案资源管理器**，然后单击**属性**。 下**配置属性**，展开的节点旁边**C/c + +** 和选择**常规**。 设置**具有公共语言运行时支持的编译**到**无公共语言运行库支持**。  
  
### <a name="to-compile-an-atl-dll-by-using-clr"></a>若要通过使用 /clr 编译 ATL DLL  
  
1.  按照"使用 /clr 编译 ATL 可执行文件"部分中的步骤。  
  
2.  下**配置属性**，展开的节点旁边**C/c + +** 和选择**预编译标头**。 设置**创建/使用预编译标头**到**不使用预编译标头**。  
  
     作为替代方法，在**解决方案资源管理器**，右键单击 Stdafx.cpp，然后单击**属性**。 下**配置属性**，展开的节点旁边**C/c + +** 和选择**常规**。 设置**具有公共语言运行时支持的编译**到**无公共语言运行库支持**。  
  
3.  对于包含 DllMain 和任何内容的文件，它调用，在**解决方案资源管理器**，右键单击该文件，然后单击**属性**。 下**配置属性**，展开的节点旁边**C/c + +** 和选择**常规**。 在右窗格中，在**项目默认值**，将其设置**具有公共语言运行时支持的编译**到**无公共语言运行库支持**。  
  
## <a name="see-also"></a>请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)