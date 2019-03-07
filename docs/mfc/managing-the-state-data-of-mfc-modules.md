---
title: 管理 MFC 模块的状态数据
ms.date: 11/19/2018
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
ms.openlocfilehash: 0cdb368dc70b73ba70b3721fecdaf47de36686d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293792"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>管理 MFC 模块的状态数据

本文讨论 MFC 模块的状态数据以及在执行流（路径代码将在执行时通过应用程序）进入和离开模块时如何更新此状态。 切换模块状态与 AFX_MANAGE_STATE 和 METHOD_PROLOGUE 宏还讨论了。

> [!NOTE]
>  此处术语“模块”指一个可执行程序，或指独立于剩下的应用程序运行、但使用 MFC DLL 的共享副本的 DLL（或 DLL 集）。 ActiveX 控件是典型的模块示例。

如下图所示，MFC 具有应用程序中所用每个模块的状态数据。 此数据的示例包括 Windows 实例句柄（用于加载资源）、指向应用程序的当前 `CWinApp` 和 `CWinThread` 对象的指针、OLE 模块引用计数和大量保留 Windows 对象句柄和对应的 MFC 对象实例之间的连接的映射。 但是，当应用程序使用多个模块时，每个模块的状态数据不在应用程序范围内。 每个模块具有其自己的 MFC 状态数据的私有副本。

![状态数据的单个模块&#40;应用程序&#41;](../mfc/media/vc387n1.gif "状态数据的单个模块的&#40;应用程序&#41;") <br/>
单模块的状态数据（应用程序）

模块的状态数据包含在结构中并且始终可通过指向所在结构的指针使用。 如下图所示，在执行流进入特定模块时，该模块的状态必须为“当前”或“有效”状态。 因此，每个线程对象具有指向应用程序的有效状态结构的指针。 时时更新此指针对管理应用程序的全局状态和维护每个模块状态的完整性至关重要。 全局状态的管理不当可能导致不可预知的应用程序行为。

![状态数据的多个模块](../mfc/media/vc387n2.gif "状态的多个模块的数据") <br/>
多模块状态数据

换句话说，每个模块负责在其所有入口点的模块状态之间正确切换。 “入口点”是执行流可以进入模块代码的所有位置。 入口点包括：

- [在 DLL 中导出的函数](../mfc/exported-dll-function-entry-points.md)

- [COM 接口的成员函数](../mfc/com-interface-entry-points.md)

- [窗口过程](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>请参阅

[常规 MFC 主题](../mfc/general-mfc-topics.md)
