---
title: "窗口过程入口点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f4e99ce38bd5ae472d688dc779bdd4ccf9fd4c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="window-procedure-entry-points"></a>窗口过程入口点
为了保护 MFC 窗口过程，模块将与特定窗口过程实现静态链接。 当模块与 MFC 链接时，链接操作将自动发生。 此窗口过程使用`AFX_MANAGE_STATE`宏正确设置有效模块状态中，然后，它调用**AfxWndProc**，这反过来委托给`WindowProc`与相应的成员函数`CWnd`-派生对象。  
  
## <a name="see-also"></a>请参阅  
 [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)

