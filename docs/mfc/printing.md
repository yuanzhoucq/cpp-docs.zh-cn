---
title: "打印 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01ee396a7866179bd140f203192d1bdcbfb4681e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="printing"></a>打印
Microsoft Windows 实现独立于设备的显示。 在 MFC 中，这意味着，相同的绘图调用，在`OnDraw`的视图类，成员函数负责绘制和其他设备，例如打印机上显示。 对于打印预览中，目标设备是模拟的打印机输出到显示器。  
  
##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>你在打印与框架的角色中的角色  
 视图类具有以下职责：  
  
-   告知框架多少页数，包括已文档。  
  
-   当系统询问打印指定的页，请绘制文档该部分。  
  
-   分配和释放任何字体或打印所需的其他图形设备接口 (GDI) 资源。  
  
-   如有必要，发送任何转义代码需要若要在打印给定的页，例如之前更改打印机模式，以更改每页基础上的打印方向。  
  
 框架的职责如下所示：  
  
-   显示**打印**对话框。  
  
-   创建[CDC](../mfc/reference/cdc-class.md)的打印机的对象。  
  
-   调用[StartDoc](../mfc/reference/cdc-class.md#startdoc)和[EndDoc](../mfc/reference/cdc-class.md#enddoc)的成员函数`CDC`对象。  
  
-   重复调用[StartPage](../mfc/reference/cdc-class.md#startpage)成员函数`CDC`对象，告知视图类应打印哪一页，并调用[EndPage](../mfc/reference/cdc-class.md#endpage)成员函数`CDC`对象。  
  
-   在适当时间视图中调用可重写函数。  
  
 以下文章介绍了框架如何支持打印和打印预览：  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [如何执行默认打印](../mfc/how-default-printing-is-done.md)  
  
-   [多页文档](../mfc/multipage-documents.md)  
  
-   [页眉和页脚](../mfc/headers-and-footers.md)  
  
-   [分配用于打印的 GDI 资源](../mfc/allocating-gdi-resources.md)  
  
-   [打印预览](../mfc/print-preview-architecture.md)  
  
## <a name="see-also"></a>请参阅  
 [打印和打印预览](../mfc/printing-and-print-preview.md)

