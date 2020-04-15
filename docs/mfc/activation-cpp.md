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
ms.openlocfilehash: 9f3fba71002a19a0be0e3429a0faeeefb7c65197
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354173"
---
# <a name="activation-c"></a>Activation (C++)

本文介绍了激活在 OLE 项目的可视化编辑中的角色。 用户在容器文档中嵌入 OLE 项后，可能需要使用它。 为此，用户双击该项目，该项将激活该项目。 激活的最常见活动是编辑。 许多当前 OLE 项在激活以进行编辑时，会导致当前框架窗口中的菜单和工具栏发生更改，以反映属于创建该项目的服务器应用程序的菜单和工具栏。 此行为称为就地激活，允许用户编辑复合文档中的任何嵌入项目，而无需离开容器文档的窗口。

还可以在单独的窗口中编辑嵌入的 OLE 项。 如果容器或服务器应用程序不支持就地激活，则会发生这种情况。 在这种情况下，当用户双击嵌入项时，服务器应用程序在单独的窗口中启动，而嵌入的项显示为其自己的文档。 用户在此窗口中编辑项。 编辑完成后，用户将关闭服务器应用程序并返回到容器应用程序。

作为替代方法，用户可以选择"打开编辑"的对象**\<>"编辑**"菜单上的"打开 **"** 命令。 这将在单独的窗口中打开对象。

> [!NOTE]
> 在单独的窗口中编辑嵌入项目是 OLE 版本 1 中的标准行为，某些 OLE 应用程序可能仅支持这种编辑风格。

就地激活可促进以文档为中心的文档创建方法。 用户可以将复合文档视为单个实体，无需在应用程序之间切换即可处理它。 但是，就地激活仅用于嵌入的项目，而不是链接项目：它们必须在单独的窗口中进行编辑。 这是因为链接项实际上存储在不同的位置。 链接项的编辑在数据的实际上下文中进行，即数据存储的位置。 在单独的窗口中编辑链接项目会提醒用户数据属于另一个文档。

MFC 不支持嵌套就地激活。 如果构建容器/服务器应用程序，并且该容器/服务器嵌入到另一个容器中并激活，则无法就地激活嵌入其中的对象。

当用户双击时，嵌入项会发生什么情况取决于为该项目定义的谓词。 有关详细信息，请参阅[激活：动词](../mfc/activation-verbs.md)。

## <a name="see-also"></a>另请参阅

[OLE](../mfc/ole-in-mfc.md)<br/>
[容器](../mfc/containers.md)<br/>
[服务器](../mfc/servers.md)
