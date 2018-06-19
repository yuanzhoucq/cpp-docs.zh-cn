---
title: 打印和打印预览 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a26bac196dbddc6c05df5850225d05f432bc566
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346251"
---
# <a name="printing-and-print-preview"></a>打印和打印预览
MFC 支持通过类的程序的文档打印和打印预览[CView](../mfc/reference/cview-class.md)。 针对基本打印和打印预览，只需重写视图类的[OnDraw](../mfc/reference/cview-class.md#ondraw)成员函数，你仍必须执行操作。 该函数可以绘制到在屏幕上，到实际的打印机，是打印机设备上下文的视图或，模拟您在屏幕上的打印机设备上下文。  
  
 你还可以添加代码来管理多页文档打印和预览，进行分页打印的文档，并向其中添加页眉和页脚。  
  
 此系列文章介绍如何打印实现在 Microsoft 基础类库 (MFC) 以及如何利用已内置于框架的打印体系结构。 文章还介绍了 MFC 如何支持简单实现打印预览功能和如何使用和修改该功能。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [打印](../mfc/printing.md)  
  
-   [打印预览体系结构](../mfc/print-preview-architecture.md)  
  
-   [示例](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)
