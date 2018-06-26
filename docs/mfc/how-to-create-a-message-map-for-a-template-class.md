---
title: 如何： 为一种模板类创建消息映射 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7867cc40ae837da5fad957b6a1d584fb7c2c4ce
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929895"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>如何：为模板类创建消息映射
MFC 中的消息映射提供了一种将 Windows 消息定向到合适的 C++ 对象实例的有效方法。 MFC 消息映射目标的示例包括应用程序类、文档和视图类、控件类等。  
  
 使用声明传统 MFC 消息映射[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏声明的消息映射，每个消息处理程序类方法，一个宏条目开始，最后[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)宏声明的消息映射的末尾。  
  
 使用的一个限制[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)结合与包含模板自变量的类使用时发生宏。 在与模板类一起使用时，此宏会导致编译时错误，因为宏展开过程中缺少模板参数。 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)宏旨在允许类包含单个模板自变量来声明其自己的消息映射。  
  
## <a name="example"></a>示例  
 考虑一个示例其中 MFC [CListBox](../mfc/reference/clistbox-class.md)类进行扩展以提供与外部数据源同步。 这里虚构`CSyncListBox`类声明，如下所示：  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 `CSyncListBox`类是单一类型描述它将使用同步的数据源上模板化。 它还声明了将参与类的消息映射的三种方法： `OnPaint`， `OnDestroy`，和`OnSynchronize`。 `OnSynchronize`方法实现，如下所示：  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 上述实现使`CSyncListBox`类来实现的任何类类型上专用化`GetCount`方法，如`CArray`， `CList`，和`CMap`。 `StringizeElement`函数是通过以下原型化模板函数：  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 通常，此类的消息映射的定义方式如下：  
  
 `BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)`  
  
 `ON_WM_PAINT()`  
  
 `ON_WM_DESTROY()`  
  
 `ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)`  
  
 `END_MESSAGE_MAP()`  
  
 其中**LBN_SYNCHRONIZE**是应用程序，如定义的自定义用户消息：  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 上面的宏映射将不进行编译，因为这样一个事实： 的模板规范`CSyncListBox`类宏展开过程将会丢失。 **BEGIN_TEMPLATE_MESSAGE_MAP**宏，因此解决了这将指定的模板参数合并到扩展的宏映射。 此类的消息映射将成为：  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 以下内容演示的示例用法`CSyncListBox`类使用`CStringList`对象：  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 若要完成测试，`StringizeElement`函数必须专用于使用`CStringList`类：  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)   
 [消息处理和映射](../mfc/message-handling-and-mapping.md)

