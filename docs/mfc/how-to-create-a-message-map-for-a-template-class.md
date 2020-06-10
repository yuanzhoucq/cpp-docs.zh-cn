---
title: 如何：为模板类创建消息映射
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 65ddc77b4e8fd466c7d651e54e93a504b4858da1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620051"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>如何：为模板类创建消息映射

MFC 中的消息映射提供了一种将 Windows 消息定向到合适的 C++ 对象实例的有效方法。 MFC 消息映射目标的示例包括应用程序类、文档和视图类、控件类等。

使用[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏声明传统 MFC 消息映射，以声明消息映射的开头、每个消息处理程序类方法的宏条目，最后[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)宏声明消息映射的结尾。

当与包含模板参数的类结合使用时，将会出现[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏的一个限制。 在与模板类一起使用时，此宏会导致编译时错误，因为宏展开过程中缺少模板参数。 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)宏旨在允许包含单个模板自变量的类声明自己的消息映射。

## <a name="example"></a>示例

假设有一个示例，其中 MFC [CListBox](reference/clistbox-class.md)类已扩展以提供与外部数据源的同步。 虚拟 `CSyncListBox` 类的声明方式如下：

[!code-cpp[NVC_MFC_CListBox#42](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

`CSyncListBox`类在一种类型上模板化，该类型描述它将与之同步的数据源。 它还声明了三个将参与类的消息映射的方法： `OnPaint` 、 `OnDestroy` 和 `OnSynchronize` 。 `OnSynchronize`方法的实现方式如下：

[!code-cpp[NVC_MFC_CListBox#43](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

上述实现允许 `CSyncListBox` 在实现方法的任何类类型上特殊化类 `GetCount` ，如 `CArray` 、 `CList` 和 `CMap` 。 `StringizeElement`函数是原型的模板函数，如下所示：

[!code-cpp[NVC_MFC_CListBox#44](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

通常，此类的消息映射的定义方式如下：

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

其中**LBN_SYNCHRONIZE**是应用程序定义的自定义用户消息，如：

[!code-cpp[NVC_MFC_CListBox#45](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

由于类的模板规范 `CSyncListBox` 在宏扩展过程中将丢失，因此以上宏映射将不会编译。 **BEGIN_TEMPLATE_MESSAGE_MAP**宏通过将指定的模板参数合并到扩展的宏映射中来解决此情况。 此类的消息映射将成为：

[!code-cpp[NVC_MFC_CListBox#46](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

下面演示使用对象的类的示例用法 `CSyncListBox` `CStringList` ：

[!code-cpp[NVC_MFC_CListBox#47](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

若要完成测试， `StringizeElement` 函数必须专门用于 `CStringList` 类：

[!code-cpp[NVC_MFC_CListBox#48](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>另请参阅

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[消息处理和映射](message-handling-and-mapping.md)
