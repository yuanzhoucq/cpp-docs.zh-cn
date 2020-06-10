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
ms.openlocfilehash: 47640a59180348bd3513013b65029a775545e211
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619186"
---
# <a name="activation-c"></a>Activation (C++)

本文介绍了在 OLE 项的可视化编辑中激活的角色。 用户在容器文档中嵌入了 OLE 项后，可能需要使用它。 若要执行此操作，用户双击该项，这会激活该项。 用于激活的最频繁的活动是编辑。 许多当前 OLE 项在被激活以进行编辑时，会导致当前框架窗口中的菜单和工具栏发生更改，以反映属于创建该项的服务器应用程序的对象。 此行为称为就地激活，允许用户编辑复合文档中的任何嵌入项，而无需离开容器文档的窗口。

还可以在单独的窗口中编辑嵌入的 OLE 项。 如果容器或服务器应用程序不支持就地激活，则会发生这种情况。 在这种情况下，当用户双击嵌入项时，将在单独的窗口中启动服务器应用程序，并且嵌入项显示为其自己的文档。 用户编辑此窗口中的项。 完成编辑后，用户会关闭服务器应用程序并返回到容器应用程序。

作为替代方法，用户可以使用 "**编辑**" 菜单上的 " ** \<object> 打开**" 命令选择 "打开编辑"。 这将在单独的窗口中打开对象。

> [!NOTE]
> 在单独的窗口中编辑嵌入项是 OLE 版本1中的标准行为，某些 OLE 应用程序可能只支持这种编辑样式。

就地激活提升了以文档为中心的方法来创建文档。 用户可以将复合文档视为单个实体，而无需在应用程序之间切换即可进行处理。 但是，就地激活仅用于嵌入项，而不用于链接项：它们必须在单独的窗口中进行编辑。 这是因为链接项实际上存储在不同的位置。 对链接项的编辑发生在数据的实际上下文中，即数据的存储位置。 在单独的窗口中编辑链接项会提醒用户数据属于其他文档。

MFC 不支持嵌套就地激活。 如果你构建容器/服务器应用程序，并且该容器/服务器嵌入另一个容器并就地激活，则它不能就地激活嵌入在其中的对象。

当用户双击嵌入项时，它会发生什么情况取决于为该项定义的谓词。 有关信息，请参阅[激活：谓词](activation-verbs.md)。

## <a name="see-also"></a>另请参阅

[OLE](ole-in-mfc.md)<br/>
[容器](containers.md)<br/>
[服务器](servers.md)
