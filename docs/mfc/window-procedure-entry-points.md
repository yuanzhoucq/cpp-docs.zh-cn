---
title: 窗口过程入口点
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 9e395ff96d27476bc2869e23139cb2d1233f02ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500914"
---
# <a name="window-procedure-entry-points"></a>窗口过程入口点

为了保护 MFC 窗口过程，模块将与特定窗口过程实现静态链接。 当模块与 MFC 链接时，链接操作将自动发生。 此窗口过程使用 AFX_MANAGE_STATE 宏来正确设置有效模块状态中，然后调用`AfxWndProc`，这反过来委托给`WindowProc`成员函数的相应`CWnd`-派生的对象。

## <a name="see-also"></a>请参阅

[管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)

