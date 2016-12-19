---
title: "打印 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文档, 打印"
  - "打印 [MFC]"
  - "打印 [MFC], 从框架"
  - "视图类, 打印操作"
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 打印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 实现 Windows 设备无关的显示。  在 MFC 中，这意味着相同的调用，如视图类的 `OnDraw` 成员函数，负责绘制显示负责在和其他设备上，如打印机。  对于打印预览，目标设备是一个模拟的打印机输出所示。  
  
##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> 在打印的效果与 Framework 的角色  
 视图类具有以下作用：  
  
-   通知框架多少页文档中。  
  
-   当要求打印指定的页，请绘制文档该部分的。  
  
-   分配并释放为打印或其他图形设备接口 \(GDI\) 资源需要的所有字体。  
  
-   如有必要，请将必需的所有逃命代码更改打印机模式，然后打印某一特定页，例如更改，逐页前的打印方向。  
  
 框架的职责如下：  
  
-   显示 **打印** 对话框。  
  
-   打印机创建一个对象。[CDC](../mfc/reference/cdc-class.md)  
  
-   调用 `CDC`、[EndDoc](../Topic/CDC::EndDoc.md)[StartDoc](../Topic/CDC::StartDoc.md) 对象的成员函数。  
  
-   重复请调用 `CDC` 对象的函数 [为 StartPage](../Topic/CDC::StartPage.md) 成员，请注意视图类的输出应页，然后调用 `CDC` 对象的成员函数。[EndPage](../Topic/CDC::EndPage.md)  
  
-   调用视图中的可重写的函数在适当的时间。  
  
 下列文章讨论框架如何支持打印和"打印预览":  
  
### 您想进一步了解什么？  
  
-   [默认打印如何完成](../mfc/how-default-printing-is-done.md)  
  
-   [多文档页](../mfc/multipage-documents.md)  
  
-   [页眉和页脚](../mfc/headers-and-footers.md)  
  
-   [分配打印的 GDI 资源](../mfc/allocating-gdi-resources.md)  
  
-   [打印预览](../mfc/print-preview-architecture.md)  
  
## 请参阅  
 [打印和打印预览](../mfc/printing-and-print-preview.md)