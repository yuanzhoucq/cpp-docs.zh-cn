---
title: 标准 Windows 消息的处理程序
ms.date: 11/04/2016
f1_keywords:
- afx_msg
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
ms.openlocfilehash: 9a136caf3a1d22151cb9cfd48e1cd3f999ab51ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370499"
---
# <a name="handlers-for-standard-windows-messages"></a>标准 Windows 消息的处理程序

标准 Windows 消息 **（WM_**） 的默认处理程序在`CWnd`类中预定义。 类库基于消息名称来命名这些处理程序的名称。 例如 **，WM_PAINT**消息的处理程序声明为`CWnd`：

`afx_msg void OnPaint();`

**afx_msg**关键字通过将处理程序与其他成员`CWnd`函数区分开来来建议C++**虚拟**关键字的效果。 但请注意，这些函数实际上都不是虚函数；它们是通过消息映射实现的。 消息映射仅取决于标准预处理器宏，而不是 C++ 语言的任何扩展。 **afx_msg**关键字在预处理后解析为空白。

若要重写基类中定义的处理程序，只需使用派生类中相同的原型定义一个函数，并为处理程序生成一个消息映射条目。 您的处理程序将“重写”任何类的基类中名称相同的任意处理程序。

在某些情况下，您的处理程序应当调用基类中的已重写处理程序，以便基类和 Windows 可处理消息。 在重写中调用基类处理程序的位置取决于环境。 有时您必须首先调用基类，有时最后调用。 有时如果您选择不处理消息，则将有条件地调用基类处理程序。 有时你应调用基类处理程序，然后根据基类处理程序返回的值或状态有条件地执行你自己的处理程序代码。

> [!CAUTION]
> 如果您打算将传入处理程序的参数传递到基类处理程序，则修改这些参数不安全。 例如，您可能很想修改`OnChar`处理程序的*nChar*参数（例如转换为大写）。 此行为相当模糊，但如果需要完成此效果，`CWnd`请使用成员函数。 `SendMessage`

当[类向导](reference/mfc-class-wizard.md)为给定消息（例如`OnCreate`**WM_CREATE**的处理程序）编写处理程序函数骨架时，如何确定重写给定消息的正确方法？ 以下示例建议处理程序首先调用基类处理程序，并在不返回 -1 的情况下继续操作。

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

按照约定，这些处理程序的名称以前缀“On”开头。 其中一些处理程序不采用任何自变量，而另一些处理程序采用几个自变量。 有些也有返回类型，而不是**无效**。 所有**WM_** 消息的默认处理程序都记录在*MFC 参考*中，作为名称以"On"开头的类`CWnd`的成员函数。 中`CWnd`的成员函数声明以**afx_msg**为预缀。

## <a name="see-also"></a>另请参阅

[声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
