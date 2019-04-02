---
title: 处理应用按钮
ms.date: 11/04/2016
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
ms.openlocfilehash: 30ee549a334a684deeb4a845f2fc49ee8bbe11db
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770832"
---
# <a name="handling-the-apply-button"></a>处理应用按钮

属性表具有标准对话框没有的功能：它们允许用户以应用关闭属性表之前进行的更改。 这是通过“应用”按钮完成的。 本文讨论您可以用于正确实现此功能的方法。

模式对话框一般将在用户单击“确定”关闭对话框时将设置应用于外部对象。 同样适用于属性表：当用户单击确定时，属性表中的新设置生效。

但是，您可能想让用户能够在不必关闭属性表对话框的情况下保存设置。 这是“应用”按钮的功能。 相对于仅应用当前活动页的当前设置，“应用”按钮会将所有属性页中的当前设置应用于外部对象。

默认情况下，“应用”按钮始终处于禁用状态。 你必须编写代码以在合适的时间启用“应用”按钮，并且你必须编写代码实现“应用”的效果，如下所述。

如果您不希望向用户提供“应用”功能，不必删除“应用”按钮。 您可以使其处于禁用状态，这在使用标准属性表支持（Windows 的未来版本中将提供）的应用程序之间将很常见。

若要报告为已修改页面并启用应用按钮，调用`CPropertyPage::SetModified( TRUE )`。 如果任何页报告“正在修改”，则“应用”按钮都将保持启用状态，无论当前活动页是否已修改都是如此。

应调用[cpropertypage:: Setmodified](../mfc/reference/cpropertypage-class.md#setmodified)每当用户更改页中的任何设置。 用户更改页中的设置时进行检测的一种方法是为每个属性页中的控件实现更改通知处理程序，例如**EN_CHANGE**或**BN_CLICKED**。

若要实现“应用”按钮的效果，属性表必须告知其所有者或应用程序中的其他外部对象，应用属性页中的当前设置。 同时，属性表应禁用应用按钮通过调用`CPropertyPage::SetModified( FALSE )`其修改应用于外部对象的所有页面。

此过程的示例，请参阅 MFC 常规示例[PROPDLG](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>请参阅

[属性表](../mfc/property-sheets-mfc.md)
