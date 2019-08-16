---
title: 分配 GDI 资源
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 672a9a2ce103ae7f53f61ae955f77276eb1d2945
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509279"
---
# <a name="allocating-gdi-resources"></a>分配 GDI 资源

此文章介绍了如何分配和解除分配打印所需的 Windows 图形设备接口 (GDI) 对象。

> [!NOTE]
>  有关详细信息, 请参阅[Gdi + SDK 文档](/windows/win32/gdiplus/-gdiplus-gdi-start)。

假设你需要使用某些字体、画笔或其他 GDI 对象进行打印，而不是用于屏幕显示。 由于它们需要的内存，因此当应用程序启动时，分配这些对象的效率将比较低。 当应用程序没有打印文档时，该内存可能需要用于其他目的。 更好的做法是：开始打印时，将它们分配；打印结束时，将它们删除。

若要分配这些 GDI 对象, 请重写[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)成员函数。 由于两个原因, 此函数非常适合此目的: 框架在每个打印作业开始时调用此函数一次, 与[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)不同, 此函数有权访问表示打印机设备的[CDC](../mfc/reference/cdc-class.md)对象驱动器. 您可以通过在视图类中定义指向 GDI 对象的成员变量 (例如, `CFont *`成员等) 来存储这些对象, 以供在打印作业时使用。

若要使用已创建的 GDI 对象, 请在[OnPrint](../mfc/reference/cview-class.md#onprint)成员函数中将其选择为打印机设备上下文。 如果文档的不同页面需要不同的 GDI 对象, 可以检查`m_nCurPage` [CPrintInfo](../mfc/reference/cprintinfo-structure.md)结构的成员, 并相应地选择 gdi 对象。 如果你需要一个 GDI 对象用于几个连续的页面，Windows 要求每次调用 `OnPrint` 时，将它选入设备上下文中。

若要解除分配这些 GDI 对象, 请重写[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)成员函数。 在每个打印作业结束时，框架会调用此函数，为你提供机会在应用程序返回到其他任务之前，释放特定于打印的 GDI 对象。

## <a name="see-also"></a>请参阅

[打印](../mfc/printing.md)<br/>
[如何执行默认打印](../mfc/how-default-printing-is-done.md)
