---
title: 通过代码向导对控件进行类型安全的访问
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: bf3ecf3016fcc15bd4ada7a15208acd9a04ca0a8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263801"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>通过代码向导对控件进行类型安全的访问

如果您熟悉 DDX 功能，可以使用中的控件属性[添加成员变量向导](../ide/add-member-variable-wizard.md)创建类型安全的访问。 这种方法是更容易创建不使用代码向导的控件。

如果只是想对控件的值的访问，DDX 将提供它。 如果你想要多个访问控件的值，使用添加成员变量向导将适当的类的成员变量添加到对话框类。 将此成员变量附加到控件属性。

成员变量可以具有而不是值属性的控件属性。 Value 属性是指从控件，如返回的数据类型`CString`或**int**。控件属性可直接访问控制通过其类型为一个控件类在 MFC 中，如数据成员`CButton`或`CEdit`。

> [!NOTE]
>  给定控件的如果您愿意，可以使用值的属性和最多一个成员变量并将控件属性的多个成员变量。 您可以只有一个 MFC 对象映射到一个控件，因为多个对象附加到一个控件或任何其他窗口中，会导致消息映射中的多义性。

此对象可用于控制对象调用任何成员函数。 此类调用会影响在对话框中的控件。 例如，复选框控件表示由变量*m_Checkbox*，类型的`CButton`，可以调用：

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

此处的成员变量*m_Checkbox*成员函数的作用相同`GetMyCheckbox`中所示[控件而无需代码向导对类型安全的访问](../mfc/type-safe-access-to-controls-without-code-wizards.md)。 如果复选框不是一个自动复选框，则仍需要一个处理程序 BN_CLICKED 控件通知消息的对话框类中单击该按钮。

有关控件的详细信息，请参阅[控件](../mfc/controls-mfc.md)。

## <a name="see-also"></a>请参阅

[对对话框中的控件进行类型安全的访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[对控件进行类型安全的访问（不使用代码向导）](../mfc/type-safe-access-to-controls-without-code-wizards.md)
