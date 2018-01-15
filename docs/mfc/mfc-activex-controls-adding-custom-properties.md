---
title: "MFC ActiveX 控件： 添加自定义属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f64154142c4c5f0fb3f24dc63120799132983880
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 控件：添加自定义属性
自定义属性不同于常用属性，因为自定义属性不会由已实现`COleControl`类。 自定义属性用于公开的某个状态或 ActiveX 控件适应程序员使用控件的外观。  
  
 本文介绍如何将自定义属性添加到使用添加属性向导的 ActiveX 控件，并说明的生成的代码修改。 包括以下主题：  
  
-   [使用添加属性向导来添加自定义属性](#_core_using_classwizard_to_add_a_custom_property)  
  
-   [添加属性向导正在更改用于自定义属性](#_core_classwizard_changes_for_custom_properties)  
  
 自定义属性可分为四种类型实现的： 成员变量、 通知、 Get/Set 方法与参数化成员变量。  
  
-   成员变量的实现  
  
     此实现中的控件类的成员变量表示该属性的状态。 当不一定要了解属性值更改时，请使用成员变量的实现。 三种类型，此实现将创建最少量的支持代码的属性。 成员变量的实现调度映射条目宏是[DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property)。  
  
-   与通知实现的成员变量  
  
     此实现由成员变量和通过添加属性向导创建的通知函数组成。 在属性值更改后通知函数自动调用由框架。 使用成员变量与通知实现在需要以属性值已更改后收到通知时。 此实现需要更多的时间，因为它要求函数调用。 此实现调度映射条目宏是[DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify)。  
  
-   Get/Set 方法实现  
  
     此实现包含一对成员函数位于控件类。 Get/Set 方法实现自动调用该获取成员函数时控件的用户请求的属性的当前值和 Set 成员函数时控件的用户请求能更改的属性。 当你需要在运行时，计算属性的值验证控件的用户更改实际的属性中之前, 传递的值或实现读取-或只写属性类型，请使用此实现。 此实现调度映射条目宏是[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)。 以下部分：[添加属性向导用于将自定义属性添加](#_core_using_classwizard_to_add_a_custom_property)，使用 CircleOffset 自定义属性来演示此实现。  
  
-   参数化的实现  
  
     添加属性向导支持参数化的实现。 （有时称为属性数组） 的参数化的属性可以用于通过您的控件的单个属性访问的一组值。 此实现调度映射条目宏是`DISP_PROPERTY_PARAM`。 有关实现此类型的详细信息，请参阅[实现参数化属性](../mfc/mfc-activex-controls-advanced-topics.md)中文章 ActiveX 控件： 高级主题。  
  
##  <a name="_core_using_classwizard_to_add_a_custom_property"></a>使用添加属性向导以添加自定义属性  
 以下过程演示如何添加自定义属性，CircleOffset，使用 Get/Set 方法的实现。 CircleOffset 自定义属性允许控件的用户偏移量从控件的边界矩形的中心的圆圈。 添加与以外 Get/Set 方法实现的自定义属性的步骤操作非常类似。  
  
 此外可以使用此相同的过程添加所需的其他自定义属性。 替换你自定义属性名称 CircleOffset 属性名称和参数。  
  
#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>若要添加使用添加属性向导 CircleOffset 自定义属性  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中，单击**添加**，然后单击**添加属性**。  
  
     这将打开[添加属性向导](../ide/names-add-property-wizard.md)。  
  
5.  在**属性名称**框中，键入`CircleOffset`。  
  
6.  对于“实现类型” ，请单击“Get/Set 方法” 。  
  
7.  在**属性类型**框中，选择**短**。  
  
8.  为 Get 和 Set 函数键入唯一名称或接受默认名称。  
  
9. 单击 **“完成”**。  
  
##  <a name="_core_classwizard_changes_for_custom_properties"></a>添加属性向导正在更改用于自定义属性  
 当你将添加 CircleOffset 自定义属性时，添加属性向导中对标头进行更改 (。H） 和实现 (。控件类的 CPP) 文件。  
  
 以下行添加到。要声明两个函数调用的 H 文件`GetCircleOffset`和`SetCircleOffset`:  
  
 [!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]  
  
 以下行添加到你的控件。IDL 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]  
  
 此行将 CircleOffset 属性分配一个特定的 ID 号，取自方法和属性列表中的添加属性向导的方法的位置。  
  
 此外，将以下行添加到调度映射 (中。控件类的 CPP 文件） 要 CircleOffset 属性映射到控件的两个处理程序函数：  
  
 [!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]  
  
 最后的实现`GetCircleOffset`和`SetCircleOffset`函数添加到控件的末尾。CPP 文件。 在大多数情况下，你将要修改 Get 函数以返回属性的值。 Set 函数通常将包含之前或在属性更改后应执行的代码。  
  
 [!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]  
  
 请注意，添加属性向导自动添加的调用，为[SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag)，正文的 Set 函数。 为已修改调用此函数将控件的标记。 如果控件已被修改，在保存容器时，将保存其新状态。 另存为控件的持久状态的一部分的属性发生更改的值时，应调用此函数。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件： 属性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控件： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 类](../mfc/reference/colecontrol-class.md)
