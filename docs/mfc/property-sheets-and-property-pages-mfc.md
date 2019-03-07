---
title: 属性表和属性页 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 7ff2851cc4ed04a64f1a49d68b6e3143b5edccd8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278753"
---
# <a name="property-sheets-and-property-pages-mfc"></a>属性表和属性页 (MFC)

MFC[对话框的](../mfc/dialog-boxes.md)可以通过将合并属性表和属性页"选项卡对话框"外观对其执行。 MFC 中称为"属性表"，这种类型的对话框中，类似于在 Microsoft Word、 Excel 和 Visual c + + 中的许多对话框中似乎包含选项卡式工作表，类似于文件文件夹中从前到后端或一组级联 windows 显示的堆栈的堆栈。 在 front 选项卡上的控件可见的;仅标记选项卡上可见的后端的选项卡。 属性表是用于管理大量的属性或非常巧妙地划分为多个组的设置特别有用。 通常情况下，一个属性表可以通过替换多个单独的对话框来简化用户界面。

从 MFC 4.0 版，开始属性表和属性页使用实现随 Windows 95 和 Windows NT 版本 3.51 及更高版本的公共控件。

属性表在类实现[CPropertySheet](../mfc/reference/cpropertysheet-class.md)并[CPropertyPage](../mfc/reference/cpropertypage-class.md) (中所述*MFC 参考*)。 `CPropertySheet` 定义总体对话框中，它可以包含多个"页"基于`CPropertyPage`。

有关创建和使用属性表的信息，请参阅主题[属性表](../mfc/property-sheets-mfc.md)。

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[MFC 中的属性表和属性页](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[交换数据](../mfc/exchanging-data.md)<br/>
[创建无模式属性表](../mfc/creating-a-modeless-property-sheet.md)<br/>
[处理应用按钮](../mfc/handling-the-apply-button.md)
