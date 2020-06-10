---
title: 活动文档服务器
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 58f2a63a8c640e6ae31640af680894763603e1d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619143"
---
# <a name="active-document-servers"></a>活动文档服务器

活动文档服务器（如 Word、Excel 或 PowerPoint）承载其他应用程序类型的文档（称为“活动文档”）。 与 OLE 嵌入对象不同（其将仅显示在另一文档的页面中），活动文档提供其创建者 - 服务器应用程序的完整接口和完整本机功能。 用户可借助喜欢的应用程序的全力创建文档（如果他们启用了活动文档），还可将生成的项目视为单一项目。

活动文档可具有多页，并且始终处于就地活动状态。 活动文档控制用户界面的一部分，将其菜单与容器的 "**文件**" 和 "**帮助**" 菜单合并。 它们占用了容器的整个编辑区并且控制打印机页面（边距、页脚等）的视图和布局。

MFC 使用文档/视图界面、命令调度映射、打印、菜单管理和注册表管理实现活动文档服务器。 [活动文档](active-documents.md)中讨论了具体的编程要求。

MFC 支持具有[CDocObjectServer](reference/cdocobjectserver-class.md)类（派生自[CCmdTarget](reference/ccmdtarget-class.md)）和[CDocObjectServerItem](reference/cdocobjectserveritem-class.md)派生自[COleServerItem](reference/coleserveritem-class.md)的活动文档。 MFC 支持具有[COleDocObjectItem](reference/coledocobjectitem-class.md)类（派生自[COleClientItem](reference/coleclientitem-class.md)）的活动文档容器。

`CDocObjectServer` 映射活动文档界面并初始化和激活活动文档。 MFC 还提供了宏来处理活动文档中的命令路由。 若要在应用程序中使用活动文档，请在 StdAfx.h 文件中包含 AfxDocOb.h。

常规 MFC 服务器将挂钩其自己的 `COleServerItem` 派生类。 如果您选中 "**微型服务器**" 或 "**完全服务器**" 复选框来提供应用程序服务器的复合文档支持，则 MFC 应用程序向导将为您生成此类。 如果还选中 "**活动文档服务器**" 复选框，则 MFC 应用程序向导将生成一个派生自的类 `CDocObjectServerItem` 。

`COleDocObjectItem` 类允许 OLE 容器成为活动文档容器。 您可以使用 MFC 应用程序向导创建活动文档容器，方法是在 MFC 应用程序向导的 "复合文档支持" 页中选中 "**活动文档容器**" 复选框。 有关详细信息，请参阅[创建活动文档容器应用程序](creating-an-active-document-container-application.md)。

## <a name="see-also"></a>另请参阅

[活动文档包容](active-document-containment.md)
