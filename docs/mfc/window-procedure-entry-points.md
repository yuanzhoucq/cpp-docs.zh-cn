---
title: 窗口过程入口点 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 315526a8f95a1d62ac89f3a76fab492c9b136715
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956377"
---
# <a name="window-procedure-entry-points"></a>窗口过程入口点
为了保护 MFC 窗口过程，模块将与特定窗口过程实现静态链接。 当模块与 MFC 链接时，链接操作将自动发生。 此窗口过程使用 AFX_MANAGE_STATE 宏正确设置有效模块状态中，然后，它调用`AfxWndProc`，这反过来委托给`WindowProc`与相应的成员函数`CWnd`-派生对象。  
  
## <a name="see-also"></a>请参阅  
 [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)

