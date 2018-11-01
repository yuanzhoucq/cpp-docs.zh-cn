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
ms.openlocfilehash: 75ff46a829bd129c7f73bf11a303a67ab1526969
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641111"
---
# <a name="sdi-and-mdi"></a>SDI 和 MDI

MFC 轻松处理单文档界面 (SDI) 和多文档界面 (MDI) 应用程序。

SDI 应用程序允许一次只有一个打开的文档框架窗口。 MDI 应用程序允许多个文档框架窗口，以在应用程序的同一实例中打开。 MDI 应用程序具有一个内的多个 MDI 子窗口，这是框架窗口，可以打开，每个包含一个单独的文档的窗口。 在某些应用程序，可以是不同的类型，如图表和电子表格 windows 子窗口。 在这种情况下，根据不同类型的 MDI 子窗口被激活，可以更改菜单栏。

> [!NOTE]
>  在 Windows 95 和更高版本，应用程序通常是 SDI 因为操作系统已采用"文档为中心"视图。

有关详细信息，请参阅[文档、 视图和框架](../mfc/documents-views-and-the-framework.md)。

## <a name="see-also"></a>请参阅

[使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)
