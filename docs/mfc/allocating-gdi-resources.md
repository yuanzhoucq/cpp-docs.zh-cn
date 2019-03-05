---
title: 分配 GDI 资源
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 5f5f6c6585217393a6008fafa875a83e67ab8016
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304998"
---
# <a name="allocating-gdi-resources"></a>分配 GDI 资源

此文章介绍了如何分配和解除分配打印所需的 Windows 图形设备接口 (GDI) 对象。

> [!NOTE]
>  有关详细信息，请参阅上的 GDI + SDK 文档： [ https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp)。

假设你需要使用某些字体、画笔或其他 GDI 对象进行打印，而不是用于屏幕显示。 由于它们需要的内存，因此当应用程序启动时，分配这些对象的效率将比较低。 当应用程序没有打印文档时，该内存可能需要用于其他目的。 更好的做法是：开始打印时，将它们分配；打印结束时，将它们删除。

若要分配这些 GDI 对象，重写[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)成员函数。 此函数非常适合于此目的有两个原因： 框架调用此函数一次的每个打印作业，并与不同开头[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)，此函数有权访问[CDC](../mfc/reference/cdc-class.md)表示打印机设备驱动程序的对象。 可以通过在指向 GDI 对象的视图类中定义成员变量在打印作业期间存储这些对象以备使用 (例如，`CFont *`成员，等等)。

若要使用已创建的 GDI 对象，它们选入打印机设备上下文中[OnPrint](../mfc/reference/cview-class.md#onprint)成员函数。 如果需要为该文档的不同页不同的 GDI 对象，您可以检查`m_nCurPage`的成员[CPrintInfo](../mfc/reference/cprintinfo-structure.md)结构，并相应地选择 GDI 对象。 如果你需要一个 GDI 对象用于几个连续的页面，Windows 要求每次调用 `OnPrint` 时，将它选入设备上下文中。

若要释放这些 GDI 对象，重写[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)成员函数。 在每个打印作业结束时，框架会调用此函数，为你提供机会在应用程序返回到其他任务之前，释放特定于打印的 GDI 对象。

## <a name="see-also"></a>请参阅

[打印](../mfc/printing.md)<br/>
[如何执行默认打印](../mfc/how-default-printing-is-done.md)
