---
title: 管理 MDI 子窗口
ms.date: 11/19/2018
f1_keywords:
- MDICLIENT
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
ms.openlocfilehash: 6e8e3d0aa51eeea112597485a9221dcba4feda87
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618363"
---
# <a name="managing-mdi-child-windows"></a>管理 MDI 子窗口

MDI 主框架窗口（每个应用程序一个）包含一个称为“MDICLIENT”窗口的特定子窗口。 MDICLIENT 窗口管理主框架窗口的工作区，本身具有子窗口：派生自的文档窗口 `CMDIChildWnd` 。 由于文档窗口是框架窗口（MDI 子窗口），因此它们也有其自己的子级。 在所有这些情况下，父窗口管理其子窗口并将一些命令转发给它们。

在 MDI 框架窗口中，框架窗口管理 MDICLIENT 窗口，与控件条结合对其进行重新定位。 反过来，MDICLIENT 窗口管理所有 MDI 子框架窗口。 下图显示 MDI 框架窗口、其 MDICLIENT 窗口与其子文档框架窗口之间的关系。

![MDI 框架窗口中的子窗口](../mfc/media/vc37gb1.gif "MDI 框架窗口中的子窗口") <br/>
MDI 框架窗口和子窗口

MDI 框架窗口还将与当前 MDI 子窗口（如果有一个）结合使用。 MDI 框架窗口在尝试处理命令消息之前，会将这些消息委派给 MDI 子窗口。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [创建文档框架窗口](creating-document-frame-windows.md)

- [框架窗口样式](frame-window-styles-cpp.md)

## <a name="see-also"></a>另请参阅

[使用框架窗口](using-frame-windows.md)
