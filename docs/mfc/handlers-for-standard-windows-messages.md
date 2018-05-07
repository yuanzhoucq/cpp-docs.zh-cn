---
title: 标准 Windows 消息的处理程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- afx_msg
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4ed4e022326d650b1012ad5244d8b18e9c789cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="handlers-for-standard-windows-messages"></a>标准 Windows 消息的处理程序
默认标准 Windows 消息的处理程序 (**WM_**) 中类预定义`CWnd`。 类库基于消息名称来命名这些处理程序的名称。 例如，`WM_PAINT` 消息的处理程序在 `CWnd` 中声明为：  
  
 `afx_msg void OnPaint();`  
  
 **Afx_msg**关键字提供建议的 c + + 的效果**虚拟**关键字 by 区分从其他处理程序`CWnd`成员函数。 但请注意，这些函数实际上都不是虚函数；它们是通过消息映射实现的。 消息映射仅取决于标准预处理器宏，而不是 C++ 语言的任何扩展。 **Afx_msg**预处理后，关键字解析为空格。  
  
 若要重写基类中定义的处理程序，只需使用派生类中相同的原型定义一个函数，并为处理程序生成一个消息映射条目。 您的处理程序将“重写”任何类的基类中名称相同的任意处理程序。  
  
 在某些情况下，您的处理程序应当调用基类中的已重写处理程序，以便基类和 Windows 可处理消息。 在重写中调用基类处理程序的位置取决于环境。 有时您必须首先调用基类，有时最后调用。 有时如果您选择不处理消息，则将有条件地调用基类处理程序。 有时你应调用基类处理程序，然后根据基类处理程序返回的值或状态有条件地执行你自己的处理程序代码。  
  
> [!CAUTION]
>  如果你打算将传入处理程序的自变量传递到基类处理程序，则修改这些自变量不安全。 例如，您可能尝试修改 `nChar` 处理程序的 `OnChar` 参数（例如，转换为大写）。 此行为非常含糊，但如果您需要实现此效果，请使用`CWnd`成员函数**SendMessage**相反。  
  
 如何确定可在属性窗口将写入指定的消息的处理程序函数的主干时覆盖指定的消息的正确方法-`OnCreate`处理程序`WM_CREATE`，例如，它概述了建议的形式重写成员函数。 下面的示例建议处理程序首先调用基类处理程序，并继续仅前提是它不返回-1。  
  
 [!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]  
  
 按照约定，这些处理程序的名称以前缀“On”开头。 其中一些处理程序不采用任何自变量，而另一些处理程序采用几个自变量。 一些处理程序还具有 `void` 之外的返回类型。 所有的默认处理程序**WM_** 消息均记录在*MFC 参考*类的成员函数作为`CWnd`名称开头"开"。 成员函数声明中的`CWnd`带有前缀**afx_msg**。  
  
## <a name="see-also"></a>请参阅  
 [声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
