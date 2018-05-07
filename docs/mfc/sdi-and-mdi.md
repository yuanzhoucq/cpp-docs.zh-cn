---
title: SDI 和 MDI |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db63efe8d7e2622610bb56f5e6885b72b705093b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="sdi-and-mdi"></a>SDI 和 MDI
MFC 使用户可轻松地与单文档界面 (SDI) 和多文档界面 (MDI) 应用程序。  
  
 SDI 应用程序允许一次只有一个打开的文档框架窗口。 MDI 应用程序允许多个文档框架窗口，才能打开应用程序的同一实例中。 MDI 应用程序了的时段内的多个 MDI 子窗口，是框架窗口，可以打开，每个包含单独的文档。 在某些应用程序，子窗口可以是不同的类型，如图表 windows 和 windows 电子表格。 在这种情况下，激活了不同类型的 MDI 子窗口，可以更改菜单栏。  
  
> [!NOTE]
>  在 Windows 95 和更高版本，应用程序通常是 SDI 因为操作系统已采用"文档为中心"视图。  
  
 有关详细信息，请参阅[文档、 视图和框架](../mfc/documents-views-and-the-framework.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)
