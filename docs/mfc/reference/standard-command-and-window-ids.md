---
title: 标准命令和窗口 ID
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: 40783bc19e51afb0e9fe9e4a429df0239a8e7f09
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907720"
---
# <a name="standard-command-and-window-ids"></a>标准命令和窗口 ID

Microsoft 基础类库定义了 Afxres.h 中的很多标准命令和窗口 ID。 这些 Id 最常用于资源编辑器和[类向导](mfc-class-wizard.md)中，用于将消息映射到处理程序函数。 所有标准命令都具有**ID_** 前缀。 例如，使用菜单编辑器时，通常会将 "文件打开" 菜单项绑定到标准 ID_FILE_OPEN 命令 ID。

对于大多数标准命令，应用程序代码不需要引用命令 ID，因为框架本身会通过其主框架类`CWinThread`（、 `CWinApp`、 `CView` `CDocument`、和）中的消息映射来处理命令。以此类推）。

除了标准命令 Id 以外，还定义了其他一些标准 Id，其前缀为**AFX_ID**。 这些 Id 包括标准窗口 Id （前缀**AFX_IDW_** ）、字符串 id （前缀**AFX_IDS_** ）和几个其他类型。

程序员很少使用以**AFX_ID**前缀开头的 id，但在重写也引用**AFX_ID**的框架函数时，可能需要引用这些 id。

ID 在此引用中不单独记录。 有关详细信息，请查看技术说明[20](../../mfc/tn020-id-naming-and-numbering-conventions.md)、 [21](../../mfc/tn021-command-and-message-routing.md)和[22](../../mfc/tn022-standard-commands-implementation.md)中的详细信息。

> [!NOTE]
>  标头文件 Afxres.h 间接包含在 Afxwin.h 中。 您必须将以下语句显式包含在应用程序的资源脚本 (.rc) 文件中：

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>请参阅

[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)
