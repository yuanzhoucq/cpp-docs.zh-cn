---
title: 活动文档服务器
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 7050b810bb5e1f0c240222cd9b8c4922ced4238a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270769"
---
# <a name="active-document-servers"></a>活动文档服务器

活动文档服务器（如 Word、Excel 或 PowerPoint）承载其他应用程序类型的文档（称为“活动文档”）。 与 OLE 嵌入对象不同（其将仅显示在另一文档的页面中），活动文档提供其创建者 - 服务器应用程序的完整接口和完整本机功能。 用户可借助喜欢的应用程序的全力创建文档（如果他们启用了活动文档），还可将生成的项目视为单一项目。

活动文档可具有多页，并且始终处于就地活动状态。 活动文档控制部分用户界面，合并其菜单与**文件**并**帮助**容器的菜单。 它们占用了容器的整个编辑区并且控制打印机页面（边距、页脚等）的视图和布局。

MFC 使用文档/视图界面、命令调度映射、打印、菜单管理和注册表管理实现活动文档服务器。 中讨论了具体的编程要求[活动文档](../mfc/active-documents.md)。

MFC 支持与活动文档[CDocObjectServer](../mfc/reference/cdocobjectserver-class.md)类，派生自[CCmdTarget](../mfc/reference/ccmdtarget-class.md)，并[CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md)派生自[COleServerItem](../mfc/reference/coleserveritem-class.md)。 MFC 支持与活动文档容器[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)类，派生自[COleClientItem](../mfc/reference/coleclientitem-class.md)。

`CDocObjectServer` 映射活动文档界面并初始化和激活活动文档。 MFC 还提供了宏来处理活动文档中的命令路由。 若要在应用程序中使用活动文档，请在 StdAfx.h 文件中包含 AfxDocOb.h。

常规 MFC 服务器将挂钩其自己的 `COleServerItem` 派生类。 MFC 应用程序向导为您生成此类，如果您选择**袖珍服务器**或**完全服务器**复选框将允许应用程序服务器复合文档支持。 如果还选择**活动文档服务器**复选框，MFC 应用程序向导生成的类派生自`CDocObjectServerItem`相反。

`COleDocObjectItem` 类允许 OLE 容器成为活动文档容器。 可以使用 MFC 应用程序向导来创建活动文档容器通过选择**活动文档容器**MFC 应用程序向导的复合文档支持页中的复选框。 有关详细信息，请参阅[创建活动文档容器应用程序](../mfc/creating-an-active-document-container-application.md)。

## <a name="see-also"></a>请参阅

[活动文档包容](../mfc/active-document-containment.md)
