---
title: "MFC ActiveX 控件：添加自定义属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控件, 属性"
  - "属性 [MFC], 自定义"
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：添加自定义属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自定义属性与常用属性与自定义属性不是 `COleControl` 类中实现。  自定义特性可用于公开 ActiveX 控件的某个状态或外观。使用控件的程序员。  
  
 本文介绍如何添加自定义属性。ActiveX 控件使用"添加属性向导并说明发生的代码更改。  主题包括：  
  
-   [使用添加属性向导的自定义属性](#_core_using_classwizard_to_add_a_custom_property)  
  
-   [添加属性向导用于自定义属性更改](#_core_classwizard_changes_for_custom_properties)  
  
 自定义属性以实现四种变化形式：成员变量，并通知，get\/set 方法的成员变量和参数化。  
  
-   实现成员变量  
  
     此实现表示属性的状态，在控件类的成员变量。  请使用变量成员的实现，知道当不重要的属性值发生更改。  三个类型，此实现将创建属性的最少支持的代码。  成员变量相等比较实现计划映射项宏是 [DISP\_PROPERTY](../Topic/DISP_PROPERTY.md)。  
  
-   通知的实现的成员变量  
  
     此实现中添加属性向导和通知函数创建的成员变量。  在属性值更改后，通知函数由框架自动调用。  中用于通知实现的成员变量，需要通知，则更改属性值。  因为它要求一函数调用，此实现需要更多时间。  此实现的计划映射项宏是 [DISP\_PROPERTY\_NOTIFY](../Topic/DISP_PROPERTY_NOTIFY.md)。  
  
-   get\/set 方法实现  
  
     此实现包含一对在控件类的成员函数。  get\/set 方法实现自动调用获取成员函数，而该控件的用户请求属性的当前值和集合成员函数，当属性更改控件的用户请求时。  请使用此实现在运行时，需要计算属性的值，该控件验证的用户传递的值。更改实际属性之前时或者实现一种或只写读的特性类型。  此实现的计划映射项宏是 [DISP\_PROPERTY\_EX](../Topic/DISP_PROPERTY_EX.md)。  以下几节，[使用添加属性向导的自定义属性](#_core_using_classwizard_to_add_a_custom_property)，使用 CircleOffset 自定义属性演示此实现。  
  
-   参数化的实现  
  
     参数化实现由添加属性向导支持。  参数化的属性 \(有时调用属性数组\) 可用于通过一个属性访问控件的一组值。  此实现的计划映射项宏是 `DISP_PROPERTY_PARAM`。  有关实现此类型的更多信息，请参见位于文章：[实现参数化的属性](../mfc/mfc-activex-controls-advanced-topics.md) 的 ActiveX 控件高级主题。  
  
##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> 使用添加属性向导的自定义属性  
 下面的过程演示添加自定义属性，CircleOffset，使用的 get\/set 方法实现。  CircleOffset 自定义属性可使控件的用户控件偏移的边框中心的圆。  添加的自定义属性的 get\/set 方法除方法外的实现非常相似。  
  
 此相同过程也可以添加所需的任何其他自定义属性。  替换 CircleOffset 属性名和参数重写自定义属性名称。  
  
#### 使用"添加属性向导，CircleOffset 添加自定义属性  
  
1.  加载控件项目。  
  
2.  在类视图中，展开控件的库节点。  
  
3.  右击控件的接口节点 \(库节点的第二个节点\) ，打开快捷菜单。  
  
4.  从快捷菜单中，单击**“添加”**，然后单击**“添加属性”**。  
  
     这会打开 [添加属性向导](../ide/names-add-property-wizard.md)。  
  
5.  在**属性名**框中，`CircleOffset`。  
  
6.  对于 **Implementation Type**，单击 **Get\/Set Methods**。  
  
7.  在 **属性类型** 框中，选择 **short**。  
  
8.  键入唯一名称 get 和 set 函数或接受默认名称。  
  
9. 单击**“完成”**。  
  
##  <a name="_core_classwizard_changes_for_custom_properties"></a> 添加属性向导用于自定义属性更改  
 当您添加 CircleOffset 自定义特性时，添加属性向导对标题进行修改 \(。H\) 和控件的实现 \(.cpp\) 文件分类。  
  
 下面一行添加到。声明两个函数 \(H 文件调用 `GetCircleOffset` 和 `SetCircleOffset`:  
  
 [!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_1.h)]  
  
 下列代码行添加到控件的 .IDL 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_2.idl)]  
  
 此行将 CircleOffset 属性特定 ID 号，将在"添加属性向导的方法和属性列表的方法的位置。  
  
 此外，下面一行添加到计划映射 \(在控件类的 .cpp 文件\) CircleOffset 属性映射到该控件的两种处理程序函数：  
  
 [!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_3.cpp)]  
  
 最后，`GetCircleOffset` 的实现和 `SetCircleOffset` 函数被添加到 .cpp 控件的文件尾。  在许多情况下，您将修改获取函数返回属性值。  集合函数通常将包含应执行或中代码，在属性更改之前。  
  
 [!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_4.cpp)]  
  
 请注意添加属性向导"自动添加一个调用，为 [SetModifiedFlag](../Topic/COleControl::SetModifiedFlag.md)，到集合函数的主体。  调用此函数。指示控件为已修改。  如果修改了新的控件，其状态会保存，当容器保存。  应调用此函数，只要属性，作为保存控件的持久状态的一部分，更改值。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)