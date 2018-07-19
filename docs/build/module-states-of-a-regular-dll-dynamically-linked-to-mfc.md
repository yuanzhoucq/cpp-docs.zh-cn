---
title: 动态链接到 MFC 的规则的 MFC DLL 的模块状态 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d15f533473ebe90d6d105ddeb57dcdcddd90e87b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369365"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>动态链接到 MFC 的规则的 MFC DLL 的模块状态
若要动态链接到 MFC DLL 的正则表达式 MFC DLL 的能力使非常复杂的某些配置。 例如，正则 MFC DLL 并使用它的可执行文件可以同时动态链接到 MFC DLL 和任何 MFC 扩展 Dll。  
  
 此配置会引起问题方面的 MFC 全局数据，如当前指向的指针`CWinApp`对象以及句柄映射。  
  
 MFC 4.0 版之前此全局数据驻留在 MFC DLL 本身，并且在进程中共享的所有模块。 使用 Win32 DLL 的每个进程获取其自己的 DLL 的数据副本，因为此方案提供跟踪每个进程的数据的简单办法。 此外，因为 AFXDLL 模型假定，将有一个`CWinApp`对象和只有一组处理过程中的地图，这些项无法在 MFC DLL 本身中进行跟踪。  
  
 但它具有动态链接到 MFC DLL 的正则 MFC DLL 的功能，它是现在可能有两个或多`CWinApp`对象进程中的 — 和的句柄映射还两个或多个集。 如何未 MFC 跟踪的它应使用哪些功能？  
  
 解决方案是为每个模块 （应用程序或常规 MFC DLL） 提供其自己的此全局状态信息副本。 因此，调用**AfxGetApp**常规 MFC DLL 返回一个指向`CWinApp`在 DLL 中，不是可执行文件中的对象。 MFC 全局数据的此每个模块的副本称为模块状态和中所述[MFC 技术说明 58](../mfc/tn058-mfc-module-state-implementation.md)。  
  
 MFC 通用窗口过程会自动切换到正确的模块的状态，因此不需要担心常规 MFC DLL 中实现任何消息处理程序。 但当你可执行文件调用到常规的 MFC DLL 时，需要将当前模块状态显式设置为 DLL 的一个。 若要执行此操作，使用**AFX_MANAGE_STATE**从 DLL 导出的每个函数中的宏。 这可通过将以下代码行添加到从 DLL 导出的函数的开头：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [动态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC 扩展 DLL](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)