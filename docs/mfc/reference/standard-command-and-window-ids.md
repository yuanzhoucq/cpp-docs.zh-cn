---
title: 标准命令和窗口 ID
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: a7f9e37702c686e13379d4034be94949f92e5e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372956"
---
# <a name="standard-command-and-window-ids"></a>标准命令和窗口 ID

Microsoft 基础类库定义了 Afxres.h 中的很多标准命令和窗口 ID。 这些 IT 在资源编辑器和[类向导](mfc-class-wizard.md)中最常用于将消息映射到处理程序函数。 所有标准命令都有**ID_** 前缀。 例如，当您使用菜单编辑器时，通常将"文件打开"菜单项绑定到标准ID_FILE_OPEN命令 ID。

对于大多数标准`CWinThread`命令，应用程序代码不需要引用命令 ID，因为框架本身通过其主框架类 （、、、、`CWinApp``CView``CDocument`等） 中的消息映射处理命令。

除了标准命令指示指示外，还定义了许多其他标准指示，这些标准指示的前缀为**AFX_ID**。 这些指示码包括标准窗口 I（前缀**AFX_IDW_）、** 字符串 I（前缀**AFX_IDS_**）和其他几个类型。

程序员很少使用以**AFX_ID**前缀开头的代号，但在重写也引用**AFX_ID**的框架函数时，您可能需要参考这些指示。

ID 在此引用中不单独记录。 您可以在技术说明[20、21](../../mfc/tn020-id-naming-and-numbering-conventions.md)和[22](../../mfc/tn022-standard-commands-implementation.md)中找到有关[21](../../mfc/tn021-command-and-message-routing.md)它们的更多信息。

> [!NOTE]
> 标头文件 Afxres.h 间接包含在 Afxwin.h 中。 您必须将以下语句显式包含在应用程序的资源脚本 (.rc) 文件中：

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
