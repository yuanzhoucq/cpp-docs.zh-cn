---
title: 如何：为模板类创建消息映射
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 676e698a899327eee8305731b5d609b5b95ece76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389497"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>如何：为模板类创建消息映射

MFC 中的消息映射提供了一种将 Windows 消息定向到合适的 C++ 对象实例的有效方法。 MFC 消息映射目标的示例包括应用程序类、文档和视图类、控件类等。

传统的 MFC 消息映射声明使用[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏声明消息映射，每个消息处理程序类方法，一个宏条目的开头和最后[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)宏声明消息映射的结尾。

一项限制[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏发生时它与包含模板自变量的类结合使用。 在与模板类一起使用时，此宏会导致编译时错误，因为宏展开过程中缺少模板参数。 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)宏旨在允许类包含单个模板参数来声明其消息映射。

## <a name="example"></a>示例

一个示例，请考虑其中 MFC [CListBox](../mfc/reference/clistbox-class.md)类扩展以提供与外部数据源同步。 虚构`CSyncListBox`类声明，如下所示：

[!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

`CSyncListBox`类是用于描述它将与同步的数据源的单个类型上模板化。 它还声明将参与类在消息映射中的三种方法： `OnPaint`， `OnDestroy`，和`OnSynchronize`。 `OnSynchronize`方法实现，如下所示：

[!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

上述实现使`CSyncListBox`类上实现的任何类类型进行特殊化`GetCount`方法，如`CArray`， `CList`，和`CMap`。 `StringizeElement`函数是一个模板函数由以下原型：

[!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

通常，此类的消息映射的定义方式如下：

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

其中**LBN_SYNCHRONIZE**是应用程序，如定义的自定义用户消息：

[!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

上面的宏映射将不会编译，因为该模板规范`CSyncListBox`类宏展开过程将会丢失。 **BEGIN_TEMPLATE_MESSAGE_MAP**宏能通过将指定的模板参数合并到扩展的宏映射解决这个问题。 此类的消息映射将成为：

[!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

下面的内容演示的示例用法`CSyncListBox`类使用`CStringList`对象：

[!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

若要完成测试`StringizeElement`函数必须进行专用化，以便使用`CStringList`类：

[!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>请参阅

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[消息处理和映射](../mfc/message-handling-and-mapping.md)
