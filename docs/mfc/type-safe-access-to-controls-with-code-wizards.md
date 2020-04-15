---
title: 通过代码向导对控件进行类型安全的访问
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: b49c1b6f21dfe5270e40649241812320303ad411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370920"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>通过代码向导对控件进行类型安全的访问

如果您熟悉 DDX 功能，则可以使用["添加成员变量向导](../ide/add-member-variable-wizard.md)"中的"控件"属性创建类型安全访问。 此方法比在没有代码向导的情况下创建控件更容易。

如果只想访问控件的值，DDX 会提供该值。 如果要执行更多操作，请使用"添加成员变量向导"将相应类的成员变量添加到对话框类中。 将此成员变量附加到 Control 属性。

成员变量可以具有 Control 属性而不是 Value 属性。 Value 属性引用从控件返回的数据类型，例如`CString`或**int**。Control 属性允许通过数据类型是 MFC 中的控制类之一（如`CButton`或`CEdit`） 的数据成员直接访问控件。

> [!NOTE]
> 对于给定控件，如果需要，可以具有具有 Value 属性的多个成员变量，并且最多具有 Control 属性的一个成员变量。 只能将一个 MFC 对象映射到控件，因为连接到控件或任何其他窗口的多个对象将导致消息映射中的歧义。

可以使用此对象调用控件对象的任何成员函数。 此类调用会影响对话框中的控件。 例如，对于由变量*m_Checkbox*表示的复选框控件`CButton`，可以调用：

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

在这里，成员变量*m_Checkbox*的作用与`GetMyCheckbox`[类型安全访问无代码向导中的控件](../mfc/type-safe-access-to-controls-without-code-wizards.md)中显示的成员函数相同。 如果复选框不是自动复选框，则单击该按钮时，仍需要BN_CLICKED控制通知消息的对话框类中的处理程序。

有关控件的详细信息，请参阅[控件](../mfc/controls-mfc.md)。

## <a name="see-also"></a>另请参阅

[对对话框中的控件进行类型安全的访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[在 MFC 中使用对话框](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[在没有代码向导的情况下对控件进行类型安全访问](../mfc/type-safe-access-to-controls-without-code-wizards.md)
