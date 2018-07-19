---
title: 扩展 Dll： 概述 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bd851b9335e2b1ecffc8873590f176d7ebb2205
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367815"
---
# <a name="mfc-extension-dlls-overview"></a>MFC 扩展 Dll： 概述
MFC 扩展 DLL 是通常实现从现有的 Microsoft 基础类库类派生的可重用类的 DLL。 MFC 扩展 Dll 是使用 MFC （也称为 MFC 的共享版本） 的动态链接库版本生成的。 仅 MFC 可执行文件 （应用程序或 MFC 的规则 Dll） 使用共享版本的 MFC 生成可以使用 MFC 扩展 DLL。 MFC 扩展 DLL，可以从 MFC 派生新的自定义类，然后提供此扩展的版本的 MFC 应用程序调用 DLL。  
  
 扩展 Dll 还可用于应用程序和 DLL 之间传递 MFC 派生的对象。 在其中创建对象的模块中存在与传递的对象关联的成员函数。 由于使用 MFC 的共享的 DLL 版本时，这些函数将正确导出，你可以自由地传递 MFC 或应用程序和 MFC 扩展 Dll 加载之间的 MFC 派生的对象指针。  
  
 满足 MFC 扩展 DLL 的基本要求的 DLL 的示例，请参阅 MFC 示例[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)。 具体而言，查看 Testdll1.cpp 和 Testdll2.cpp 文件。  
  
 请注意，术语 AFXDLL 不再使用 Visual c + + 文档中。 MFC 扩展 DLL 具有以前 AFXDLL 作为相同的特征。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [初始化 MFC 扩展 DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [MFC 扩展 DLL](../build/extension-dlls.md)  
  
-   [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)  
  
-   [静态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [创建 MFC DLL](../mfc/reference/mfc-dll-wizard.md)  
  
## <a name="see-also"></a>请参阅  
 [DLL 的类型](../build/kinds-of-dlls.md)