---
title: "分配 GDI 资源 | Microsoft Docs"
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
  - "GDI 对象, 打印期间分配"
  - "打印 [MFC], 分配 GDI 资源"
  - "资源 [MFC], 打印"
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 分配 GDI 资源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此文章介绍了如何分配和解除分配打印所需的 Windows 图形设备接口 \(GDI\) 对象。  
  
> [!NOTE]
>  GDI\+ 随 Windows XP 附带，可用作 Windows NT 4.0 SP6、Windows 2000、Windows 98 和 Windows Me 的可再发行组件。  若要下载最新可再发行组件，请参阅 [http:\/\/www.microsoft.com\/msdownload\/platformsdk\/sdkupdate\/psdkredist.htm](http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm)。  有关详细信息，请参阅 MSDN 中的 GDI\+ SDK 文档：[http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/gdicpp\/GDIPlus\/GDIPlus.asp](http://msdn.microsoft.com/library/default.asp?url=/library/gdicpp/GDIPlus/GDIPlus.asp)。  
  
 假设你需要使用某些字体、画笔或其他 GDI 对象进行打印，而不是用于屏幕显示。  由于它们需要的内存，因此当应用程序启动时，分配这些对象的效率将比较低。  当应用程序没有打印文档时，该内存可能需要用于其他目的。  更好的做法是：开始打印时，将它们分配；打印结束时，将它们删除。  
  
 若要分配这些 GDI 对象，请重写 [OnBeginPrinting](../Topic/CView::OnBeginPrinting.md) 成员函数。  此函数很适合于此目的，有两个原因：在每个打印作业开始时，框架调用此函数一次，并且与 [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 不同，此函数有权访问表示打印机设备驱动程序的 [CDC](../mfc/reference/cdc-class.md) 对象。  可在打印作业期间通过在指向 GDI 对象（例如，**CFont \*** 成员等等）的视图类中定义成员变量来存储这些对象以备使用。  
  
 若要使用已创建的 GDI 对象，在 [OnPrint](../Topic/CView::OnPrint.md) 成员函数中将它们选入打印机设备上下文中。  如果你需要不同的 GDI 对象用于文档的不同页面，你可以检查 [CPrintInfo](../mfc/reference/cprintinfo-structure.md) 结构的 `m_nCurPage` 成员，并相应地选择 GDI 对象。  如果你需要一个 GDI 对象用于几个连续的页面，Windows 要求每次调用 `OnPrint` 时，将它选入设备上下文中。  
  
 若要释放这些 GDI 对象，请重写 [OnEndPrinting](../Topic/CView::OnEndPrinting.md) 成员函数。  在每个打印作业结束时，框架会调用此函数，为你提供机会在应用程序返回到其他任务之前，释放特定于打印的 GDI 对象。  
  
## 请参阅  
 [打印](../mfc/printing.md)   
 [如何执行默认打印](../mfc/how-default-printing-is-done.md)