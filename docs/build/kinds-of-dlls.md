---
title: "类型的 Dll |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47ce4a9264a59f88f22cd40bc3b6d6620c9702c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="kinds-of-dlls"></a>DLL 类型
本主题提供信息来帮助你确定要生成 dll 的类型。  
  
##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>不同类型的 Dll 可用  
 使用 Visual c + +，您可以构建在 C 或 c + + 中的 Win32 Dll，不使用 Microsoft 基础类 (MFC) 库。 你可以使用 Win32 应用程序向导创建的非 MFC DLL 项目。  
  
 在 MFC 库自身可用，则在任一静态链接库或大量使用 MFC DLL 向导 Dll 中。 如果 DLL 使用 MFC，则 Visual c + + 支持三种不同的 DLL 开发方案：  
  
-   生成正则表达式 MFC DLL，该服务以静态方式链接 MFC  
  
-   生成正则表达式 MFC DLL，该服务动态链接 MFC  
  
-   哪个生成 MFC 扩展 DLL，始终动态链接 MFC  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)  
  
-   [静态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC 扩展 DLL：概述](../build/extension-dlls-overview.md)  
  
-   [哪种类型的 DLL 用于](#_core_which_kind_of_dll_to_use)  
  
##  <a name="_core_which_kind_of_dll_to_use"></a>确定哪种类型的使用的 DLL  
 如果您的 DLL 不使用 MFC，使用 Visual c + + 生成非 MFC Win32 DLL。 链接到 MFC 的 DLL，（静态或动态） 需要占用大量磁盘空间和内存。 除非 DLL 实际上使用 MFC，不应链接到 MFC。  
  
 如果您的 DLL 将使用 MFC，并且将由 MFC 或非 MFC 应用程序，必须生成动态链接到 MFC 的正则 MFC DLL 或静态链接到 MFC 的正则 MFC DLL。 在大多数情况下，你可能想要使用动态链接到 MFC，因为这种 DLL 文件大小要小得多，且会在内存中使用共享的版本的 MFC 节省大量的规则 MFC DLL。 如果静态链接到 MFC，您的 DLL 的文件大小将会更大并可能占用额外内存，因为它将加载其自己的 MFC 库代码的私有副本。  
  
 生成动态链接到 MFC 的 DLL 速度快比构建静态链接到 MFC，因为它不是链接 MFC 本身所需的 DLL。 这是在调试版本链接器必须在其中压缩的调试信息中尤其如此。 通过链接一个 DLL，它已包含的调试信息，没有调试信息变少，若要在 DLL 内压缩。  
  
 动态链接到 MFC 的一个缺点是，你必须将分发共享的 Dll Mfcx0.dll 和 Msvcrxx.dll （或类似的文件） 与您的 DLL。 MFC Dll 是自由地重新发布，但你仍必须将安装 Dll 在你的安装程序。 此外，你必须将发运 Msvcrxx.dll，其中包含你的程序和 MFC Dll 本身使用 C 运行时库。  
  
 如果您的 DLL 将仅由 MFC 可执行文件，可以生成正则 MFC DLL 或 MFC 扩展 DLL 之间选择。 如果您的 DLL 实现可重复使用从现有的 MFC 类派生的类或你需要应用程序和 DLL 之间传递 MFC 派生的对象，则必须生成 MFC 扩展 DLL。  
  
 如果您的 DLL 动态链接到 MFC，可能与您的 DLL 重新分发 MFC Dll。 此体系结构很适合用于共享多个可执行文件以节省磁盘空间和最大程度减少内存使用量之间类库。  
  
 之前的版本 4.0 中，使用 MFC 的 Dll 的 Visual c + + 仅支持两种： USRDLLs 和 AFXDLLs。 静态链接到 MFC 的规则 MFC Dll 具有以前的 USRDLL 作为相同的特征。 MFC 扩展 Dll 具有以前 AFXDLLs 作为相同的特征。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)  
  
-   [静态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC 扩展 DLL：概述](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)