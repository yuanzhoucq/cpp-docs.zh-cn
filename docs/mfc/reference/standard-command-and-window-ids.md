---
title: 标准命令和窗口 Id |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72b50108a9b880961f0dd8bcded1126a635fb9e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="standard-command-and-window-ids"></a>标准命令和窗口 ID
Microsoft 基础类库定义了 Afxres.h 中的很多标准命令和窗口 ID。 这些 ID 在资源编辑器和“属性”窗口中最常使用，用来将消息映射到处理程序函数。 所有标准命令都有**ID_** 前缀。 例如，当使用菜单编辑器时，你通常将绑定文件打开的菜单项到标准`ID_FILE_OPEN`命令 id。  
  
 对于大多数标准命令，应用程序代码不需要引用命令 ID，因为框架本身通过其主框架类中的消息映射命令 ( `CWinThread`， `CWinApp`，< c41> `CView` ， **CDocument**，依次类推)。  
  
 除了标准命令 Id 之外还具有前缀定义大量的其他标准 Id 的**AFX_ID**。 这些 Id 包括标准窗口 Id (前缀**AFX_IDW_**)，字符串 Id (前缀**AFX_IDS_**)，和若干其他类型。  
  
 开头的 Id **AFX_ID**前缀很少使用程序员提供的但你可能需要重写也引用框架函数时，请参考这些 Id **AFX_ID**s。  
  
 ID 在此引用中不单独记录。 你可以找到它们的详细信息在技术说明[20](../../mfc/tn020-id-naming-and-numbering-conventions.md)， [21](../../mfc/tn021-command-and-message-routing.md)，和[22](../../mfc/tn022-standard-commands-implementation.md)。  
  
> [!NOTE]
>  标头文件 Afxres.h 间接包含在 Afxwin.h 中。 您必须将以下语句显式包含在应用程序的资源脚本 (.rc) 文件中：  
  
 [!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
