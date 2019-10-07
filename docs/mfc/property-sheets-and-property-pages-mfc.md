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
ms.openlocfilehash: 5d4fd1c957b7f4d0d6ad10379a448309743aa11a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685075"
---
# <a name="property-sheets-and-property-pages-mfc"></a>属性表和属性页 (MFC)

MFC[对话框](../mfc/dialog-boxes.md)可以通过结合属性表和属性页来执行 "选项卡对话框"。 在 MFC 中称为 "属性表"，这种对话框类似于 Microsoft Word、Excel 和视觉对象C++中的多个对话框，它显示为包含一组选项卡式表，就像从前到后显示的文件文件夹堆栈或一组层叠窗口。 前一选项卡上的控件可见;"标签" 选项卡上只有 "标签" 选项卡才可见。 属性表对于管理很多组中相当简单的大量属性或设置特别有用。 通常，一个属性表可以通过替换几个单独的对话框来简化用户界面。

自 MFC 版本4.0 开始，属性表和属性页使用 Windows 95 和 Windows NT 3.51 及更高版本附带的公共控件来实现。

属性表通过类[CPropertySheet](../mfc/reference/cpropertysheet-class.md)和[CPropertyPage](../mfc/reference/cpropertypage-class.md)实现（在*MFC 参考*中进行了描述）。 `CPropertySheet` 定义整体对话框，该对话框可包含多个基于 `CPropertyPage` 的 "页面"。

有关创建和使用属性表的信息，请参阅主题[属性表](../mfc/property-sheets-mfc.md)。

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[使用 MFC 中的对话框](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[MFC 中的属性表和属性页](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[交换数据](../mfc/exchanging-data.md)<br/>
[创建无模式属性表](../mfc/creating-a-modeless-property-sheet.md)<br/>
[处理应用按钮](../mfc/handling-the-apply-button.md)
