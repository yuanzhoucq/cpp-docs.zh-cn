---
title: 页眉和页脚 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c82df1a77cdbf677a6b5e6f84c371da243b9b08d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348245"
---
# <a name="headers-and-footers"></a>页眉和页脚
本文说明如何将页眉和页脚添加到打印文档。  
  
 当您在屏幕上查看文档时，文档的名称和您在文档中的当前位置通常显示在标题栏和状态栏中。 在查看文档的打印副本时，在页眉或页脚显示名称和页码很有用。 这是一种常用方法，采用此方法后，甚至是“所见即所得”程序执行打印和屏幕显示的方式都不同。  
  
 [OnPrint](../mfc/reference/cview-class.md#onprint)成员函数是打印页眉或页脚，因为每个页上，为调用，并且仅用于打印，不是用于屏幕显示调用的合适位置。 您可以定义单独的函数来打印页眉或页脚，并从 `OnPrint` 将其传入打印机设备上下文。 你可能需要调整窗口原点或之前调用的范围[OnDraw](../mfc/reference/cview-class.md#ondraw)以避免让页眉或页脚的页重叠的正文。 您可能还必须修改 `OnDraw`，因为页容纳的文档的数量的可能减少。  
  
 补偿页眉或页脚占用的区域是使用的一种方法**m_rectDraw**的成员[CPrintInfo](../mfc/reference/cprintinfo-structure.md)。 每打印一页，就会使用该页的可用区域初始化此成员。 如果在打印页的正文前打印页眉或页脚，则可以减少中存储的矩形的大小**m_rectDraw**来页眉或页脚占用的区域。 然后`OnPrint`可以指**m_rectDraw**找出多少区域保持用于打印页的正文。  
  
 标头，或任何其他目的，不能打印[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)，因为之前调用`StartPage`成员函数[CDC](../mfc/reference/cdc-class.md)已调用。 此时，打印机设备上下文被视为位于页边界上。 您只能从 `OnPrint` 成员函数执行打印。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [打印多页文档](../mfc/multipage-documents.md)  
  
-   [分配用于打印的 GDI 资源](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>请参阅  
 [打印](../mfc/printing.md)

