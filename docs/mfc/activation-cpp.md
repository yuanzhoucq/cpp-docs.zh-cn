---
title: Activation (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
ms.openlocfilehash: a6009e5209ce71c6eed28faff2f55792a64de408
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276944"
---
# <a name="activation-c"></a>Activation (C++)

本文介绍 visual 编辑 OLE 项中的激活的角色。 用户具有在容器文档中嵌入 OLE 项后，它可能需要使用。 若要执行此操作，用户，请双击该项目，将激活该项。 编辑最频繁的激活活动。 许多当前 OLE 项，以进行编辑，激活时导致在当前的框架窗口，若要更改以反映属于创建项的服务器应用程序中的菜单和工具栏。 此行为，已知为就地激活，允许用户无需离开容器文档窗口中编辑任何嵌入复合文档项。

还有可能要编辑一个单独的窗口中嵌入的 OLE 项。 如果容器或服务器应用程序不支持就地激活，则会发生这种情况。 在这种情况下，当用户双击嵌入的项时，在一个单独的窗口中启动服务器应用程序和嵌入的项将显示为其自己的文档。 用户编辑此窗口中的项。 编辑完成后，用户关闭服务器应用程序，并返回到容器应用程序。

作为替代方法，用户可以选择"打开编辑"与**\<对象 > 打开**命令**编辑**菜单。 这将在单独的窗口中打开对象。

> [!NOTE]
>  编辑嵌入的项单独的窗口中的 OLE，版本 1 中的标准行为，某些 OLE 应用程序可能支持仅这种样式的编辑。

就地激活将升级文档创建文档为中心的方法。 用户可以将复合文档作为单个实体，而无需切换应用程序之间处理它。 但是，在就地激活仅用于嵌入项，不适用于链接的项： 必须在单独的窗口中编辑这些。 这是因为链接的项实际上存储在其他位置。 编辑链接的项目会的发生的数据，也就是说，实际的上下文中存储数据。 编辑一个单独的窗口中的链接的项提醒的用户的数据属于另一个文档。

MFC 不支持嵌套的就地激活。 如果生成容器/服务器应用程序，并且容器/服务器嵌入在另一个容器和就地激活，它不能就地激活嵌入对象。

当用户双击它，嵌入项会发生什么情况取决于为项定义的谓词。 有关信息，请参阅[激活：谓词](../mfc/activation-verbs.md)。

## <a name="see-also"></a>请参阅

[OLE](../mfc/ole-in-mfc.md)<br/>
[容器](../mfc/containers.md)<br/>
[服务器](../mfc/servers.md)
