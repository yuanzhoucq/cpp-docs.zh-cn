---
title: 添加 ATL 消息处理程序
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
ms.openlocfilehash: cc7631ac9e02891cee725b47133a273e756759d6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302450"
---
# <a name="adding-an-atl-message-handler"></a>添加 ATL 消息处理程序

若要添加到控件的消息处理程序 （处理 Windows 消息的成员函数），首先在类视图中选择的控件。 然后打开**属性**窗口中，选择**消息**图标，然后单击下拉列表在相反的必需的消息框中的控制。 这将在控件的标头文件和控件的.cpp 文件中的处理程序的主干实现中添加消息处理程序的声明。 它还将添加消息映射，并为处理程序添加一个条目。

在 ATL 中添加消息处理程序是类似于 MFC 类添加消息处理程序。 请参阅[添加 MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)有关详细信息。

以下条件仅适用于添加 ATL 消息处理程序：

- 消息处理程序遵循相同的命名约定为 MFC。

- 新的消息映射条目添加到主消息映射。 该向导无法识别替换消息映射和链接。

## <a name="see-also"></a>请参阅

[实现窗口](../atl/implementing-a-window.md)
