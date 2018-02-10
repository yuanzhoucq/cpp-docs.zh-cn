---
title: "分配 GDI 资源 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ef6b784a04b7be29b470b92aa09bef8bda449e2
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="allocating-gdi-resources"></a>分配 GDI 资源
此文章介绍了如何分配和解除分配打印所需的 Windows 图形设备接口 (GDI) 对象。  
  
> [!NOTE]
>  有关详细信息，请参阅在 GDI + SDK 文档： [http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp](http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp)。  
  
 假设你需要使用某些字体、画笔或其他 GDI 对象进行打印，而不是用于屏幕显示。 由于它们需要的内存，因此当应用程序启动时，分配这些对象的效率将比较低。 当应用程序没有打印文档时，该内存可能需要用于其他目的。 更好的做法是：开始打印时，将它们分配；打印结束时，将它们删除。  
  
 若要分配这些 GDI 对象，重写[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)成员函数。 此函数很适合于此目的，两个原因： 框架调用此函数一次每个打印作业，而不同于开头[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)，此函数有权访问[CDC](../mfc/reference/cdc-class.md)表示打印机设备驱动程序的对象。 你可以通过在指向 GDI 对象的视图类中定义成员变量在打印作业期间存储这些对象以备使用 (例如， **CFont \*** 成员，等等)。  
  
 若要使用已创建的 GDI 对象，它们选入打印机设备上下文中[OnPrint](../mfc/reference/cview-class.md#onprint)成员函数。 如果你需要不同的 GDI 对象用于文档的不同页面，你可以检查`m_nCurPage`的成员[CPrintInfo](../mfc/reference/cprintinfo-structure.md)结构并相应地选择 GDI 对象。 如果你需要一个 GDI 对象用于几个连续的页面，Windows 要求每次调用 `OnPrint` 时，将它选入设备上下文中。  
  
 若要释放这些 GDI 对象，则请重写[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)成员函数。 在每个打印作业结束时，框架会调用此函数，为你提供机会在应用程序返回到其他任务之前，释放特定于打印的 GDI 对象。  
  
## <a name="see-also"></a>请参阅  
 [打印](../mfc/printing.md)   
 [如何执行默认打印](../mfc/how-default-printing-is-done.md)

