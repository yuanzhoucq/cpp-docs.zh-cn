---
title: SDI 和 MDI
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
ms.openlocfilehash: 9730e7baf9589c4b05a60703c619aae2e941bdec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372759"
---
# <a name="sdi-and-mdi"></a>SDI 和 MDI

MFC 便于使用单文档接口 （SDI） 和多文档接口 （MDI） 应用程序。

SDI 应用程序一次只允许一个打开的文档框架窗口。 MDI 应用程序允许在应用程序的同一实例中打开多个文档框架窗口。 MDI 应用程序有一个窗口，其中可以打开多个 MDI 子窗口（即框架窗口本身），每个窗口包含单独的文档。 在某些应用程序中，子窗口可以是不同类型的，例如图表窗口和电子表格窗口。 在这种情况下，菜单栏可以随着不同类型的 MDI 子窗口的激活而更改。

> [!NOTE]
> 在 Windows 95 及更高版本下，应用程序通常是 SDI，因为操作系统采用了"以文档为中心的"视图。

有关详细信息，请参阅[文档、视图和框架](../mfc/documents-views-and-the-framework.md)。

## <a name="see-also"></a>另请参阅

[使用类为 Windows 编写应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)
