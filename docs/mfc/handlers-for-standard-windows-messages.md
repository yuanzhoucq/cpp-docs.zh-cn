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
ms.openlocfilehash: 4f512c3b9a7fce5cddd582fa774742d2b1ac0967
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907432"
---
# <a name="handlers-for-standard-windows-messages"></a>标准 Windows 消息的处理程序

标准 Windows 消息（**WM_** ）的默认处理程序是在类`CWnd`中预定义的。 类库基于消息名称来命名这些处理程序的名称。 例如， **WM_PAINT**消息的处理程序在中`CWnd`声明为：

`afx_msg void OnPaint();`

**Afx_msg**关键字通过区分来自其他`CWnd`成员函数C++的处理程序来建议**虚拟**关键字的影响。 但请注意，这些函数实际上都不是虚函数；它们是通过消息映射实现的。 消息映射仅取决于标准预处理器宏，而不是 C++ 语言的任何扩展。 在预处理后， **afx_msg**关键字解析为空白。

若要重写基类中定义的处理程序，只需使用派生类中相同的原型定义一个函数，并为处理程序生成一个消息映射条目。 您的处理程序将“重写”任何类的基类中名称相同的任意处理程序。

在某些情况下，您的处理程序应当调用基类中的已重写处理程序，以便基类和 Windows 可处理消息。 在重写中调用基类处理程序的位置取决于环境。 有时您必须首先调用基类，有时最后调用。 有时如果您选择不处理消息，则将有条件地调用基类处理程序。 有时你应调用基类处理程序，然后根据基类处理程序返回的值或状态有条件地执行你自己的处理程序代码。

> [!CAUTION]
>  如果您打算将传入处理程序的参数传递到基类处理程序，则修改这些参数不安全。 例如，你可能想要修改`OnChar`处理程序的*nChar*参数（例如，转换为大写）。 此行为相当难懂，但如果您需要实现此效果，请`CWnd`改用成员函数。 `SendMessage`

如何在[类向导](reference/mfc-class-wizard.md)为给定消息编写处理程序函数的主干时确定重写给定消息的正确方法（ `OnCreate`例如， **WM_CREATE**的处理程序），以建议重写的成员函数。 下面的示例建议处理程序首先调用基类处理程序，并仅在不返回-1 的情况下继续。

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

按照约定，这些处理程序的名称以前缀“On”开头。 其中一些处理程序不采用任何自变量，而另一些处理程序采用几个自变量。 有些也有**void**以外的返回类型。 所有**WM_** 消息的默认处理程序在*MFC 引用*中记录为类`CWnd`的成员函数，其名称以 "On" 开头。 中`CWnd`的成员函数声明以**afx_msg**为前缀。

## <a name="see-also"></a>请参阅

[声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
