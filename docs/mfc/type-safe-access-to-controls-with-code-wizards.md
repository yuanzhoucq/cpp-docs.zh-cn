---
title: 通过代码向导对控件进行类型安全的访问
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: bfbc27dbcdeeb38c40f5d989bacd65a23198d4f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213965"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>通过代码向导对控件进行类型安全的访问

如果你熟悉 DDX 功能，则可以使用[添加成员变量向导](../ide/add-member-variable-wizard.md)中的控件属性创建类型安全的访问。 此方法比不用代码向导创建控件更容易。

如果只是想要访问控件的值，DDX 会提供它。 如果要执行的操作不仅仅是访问控件的值，请使用添加成员变量向导将相应类的成员变量添加到对话框类。 将此成员变量附加到控件属性。

成员变量可以具有控件属性而不是值属性。 值属性是指从控件返回的数据类型，例如 `CString` 或 **`int`** 。 通过控件属性，可通过其类型为 MFC 中的控件类之一（如或）的数据成员直接访问控件 `CButton` `CEdit` 。

> [!NOTE]
> 对于给定的控件，你可以根据需要，使用具有值属性的多个成员变量，并且最多有一个具有控件属性的成员变量。 您只能将一个 MFC 对象映射到一个控件，因为附加到控件的多个对象或任何其他窗口会导致消息映射中出现歧义。

您可以使用此对象为控制对象调用任何成员函数。 此类调用会影响对话框中的控件。 例如，对于由类型为的变量*m_Checkbox*表示的复选框控件，可以 `CButton` 调用：

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

此处的成员变量*m_Checkbox*与在 `GetMyCheckbox` [不使用代码向导的控件的类型安全访问](../mfc/type-safe-access-to-controls-without-code-wizards.md)中显示的成员函数的作用相同。 如果复选框不是自动复选框，则在单击该按钮时，您仍需要在对话框类中为 BN_CLICKED 控制通知消息提供一个处理程序。

有关控件的详细信息，请参阅[控件](../mfc/controls-mfc.md)。

## <a name="see-also"></a>另请参阅

[对对话框中的控件进行类型安全的访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[在 MFC 中使用对话框](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[不使用代码向导对控件进行类型安全的访问](../mfc/type-safe-access-to-controls-without-code-wizards.md)
