---
title: "MFC ActiveX 控件：在 ActiveX 控件中使用图片 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LPPICTUREDISP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnDraw 方法, MFC ActiveX 控件"
  - "MFC ActiveX 控件, 图片"
  - "OnDraw 方法"
  - "OnResetState 方法"
  - "CLSID_CPicturePropPage"
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC ActiveX 控件：在 ActiveX 控件中使用图片
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍常见的图片类型以及如何在 ActiveX 控件中实现该图片类型。 包括以下主题：  
  
-   [自定义图片属性的概述](#_core_overview_of_custom_picture_properties)  
  
-   [在 ActiveX 控件中实现自定义图片属性](#_core_implementing_a_custom_picture_property_in_your_activex_control)  
  
-   [向控件项目添加内容](#_core_additions_to_your_control_project)  
  
##  <a name="_core_overview_of_custom_picture_properties"></a> 自定义图片属性的概述  
 图片类型是部分 ActiveX 控件常见的一组类型中的一种。 图片类型处理元文件、位图或图标，并允许用户指定要在 ActiveX 控件中显示的图片。 自定义图片属性使用图片对象以及允许控制用户访问图片属性的 Get\/Set 函数实现。 控制用户可通过常用图片属性页访问自定义图片属性。  
  
 除标准图片类型外，还提供字体和颜色类型。 有关如何在 ActiveX 控件中使用标准字体类型的详细信息，请参阅 [MFC ActiveX 控件：使用字体](../mfc/mfc-activex-controls-using-fonts.md)一文。  
  
 ActiveX 控件类提供了若干组件，可用于在控件内实现图片属性。 这些组件包括：  
  
-   [CPictureHolder](../mfc/reference/cpictureholder-class.md) 类。  
  
     通过该类，可轻松访问自定义图片属性所显示项的图片对象和功能。  
  
-   支持 **LPPICTUREDISP** 类型的属性，并通过 Get\/Set 函数实现。  
  
     通过“类视图”，可以快速添加一个或多个支持图片类型的自定义属性。 有关如何通过“类视图”添加 ActiveX 控件属性的详细信息，请参阅 [MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)一文。  
  
-   属性页用于操作控件的一个或多个图片属性。  
  
     此属性页是 ActiveX 控件可以使用的一组常用属性页的一部分。 有关 ActiveX 控件属性页的详细信息，请参阅 [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)一文  
  
##  <a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a> 在 ActiveX 控件中实现自定义图片属性  
 完成本部分中概述的步骤后，该控件将可以显示用户选定的图片。 用户可以通过属性页更改显示的图片，该属性页显示当前图片并具有“浏览”按钮，可让用户选择其他图片。  
  
 自定义图片属性的实现过程与其他属性类似，主要区别在于自定义属性必须支持图片类型。 由于图片属性的项必须由 ActiveX 控件绘制，因此在完全实现该属性之前，必须对其进行大量的添加和修改。  
  
 若要实现自定义图片属性，必须执行以下操作：  
  
-   [向控件项目添加代码](#_core_additions_to_your_control_project)。  
  
     必须添加标准图片属性页 ID、`CPictureHolder` 类型的数据成员，以及包含 Get\/Set 实现的 **LPPICTUREDISP** 类型的自定义属性。  
  
-   [修改控件类中的若干函数](#_core_modifications_to_your_control_project)。  
  
     对用于绘制 ActiveX 控件的若干函数进行修改。  
  
##  <a name="_core_additions_to_your_control_project"></a> 向控件项目添加内容  
 若要添加标准图片属性页的属性页 ID，请在控件实现文件 \(.CPP\) 中的 `BEGIN_PROPPAGEIDS` 宏后插入下面一行：  
  
 [!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]  
  
 还必须以 1 为增量逐渐增加 `BEGIN_PROPPAGEIDS` 宏的计数参数。 下面一行阐释了这一点：  
  
 [!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]  
  
 若要将 `CPictureHolder` 数据成员添加到控件类，请在控件头文件 \(.H\) 中的控件类声明的受保护部分下插入下面一行：  
  
 [!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]  
  
 不必对数据成员 `m_pic` 命名；可以使用任何名称。  
  
 接下来，添加支持图片类型的自定义属性：  
  
#### 使用“添加属性向导”添加自定义图片属性  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中选择“添加”，然后选择“添加属性”。  
  
5.  在“属性名称”框中，键入属性名称。 本过程中使用 `ControlPicture` 作为示例。  
  
6.  在“属性类型”框中，选择“IPictureDisp\*”作为属性类型。  
  
7.  对于“实现类型”，请单击“Get\/Set 方法”。  
  
8.  为 Get 和 Set 函数键入唯一名称或接受默认名称。 （在本例中，使用默认名称 `GetControlPicture` 和 `SetControlPicture`。）  
  
9. 单击**“完成”**。  
  
 “添加属性向导”在控件头文件 \(.H\) 的调度映射注释之间添加了以下代码：  
  
 [!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]  
  
 此外，还在控件实现文件 \(.CPP\) 的调度映射中插入了以下代码：  
  
 [!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]  
  
 “添加属性向导”还在控件实现文件中添加了以下两个存根函数：  
  
 [!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]  
  
> [!NOTE]
>  你的控件类和函数名称可能与上面的示例不同。  
  
###  <a name="_core_modifications_to_your_control_project"></a> 修改控件项目的内容  
 对控件项目进行必要的添加后，需要修改几个影响 ActiveX 控件的呈现的函数。 这些函数、`OnResetState`、`OnDraw` 以及自定义属性的 Get\/Set 函数位于控件实现文件中。 （注意，在本例中，控件类名为 `CSampleCtrl`、`CPictureHolder` 数据成员名为 `m_pic`，而自定义图片属性名称为 `ControlPicture`。）  
  
 在控件的 `OnResetState` 函数中，在 `COleControl::OnResetState` 的调用后添加以下可选行：  
  
 [!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]  
  
 这会将控件的图片设置为空白图片。  
  
 若要正确绘制图片，请确保在控件的 `OnDraw` 函数中调用 [CPictureHolder::Render](../Topic/CPictureHolder::Render.md)。 按下面的示例修改函数：  
  
 [!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]  
  
 在控件的自定义图片属性的 Get 函数中，添加下面一行：  
  
 [!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]  
  
 在控件的自定义图片属性的 Set 函数中，添加下面一行：  
  
 [!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]  
  
 图片属性必须设置为永久属性，以确保设计时添加的信息将在运行时显示。 将下面一行添加到 `COleControl` 派生类的 `DoPropExchange` 函数：  
  
 [!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/CPP/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]  
  
> [!NOTE]
>  你的类和函数名称可能与上面的示例不同。  
  
 完成修改后，重新生成项目以整合自定义图片属性的新功能并使用测试容器对新属性进行测试。 请参阅[使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)了解有关如何访问测试容器的信息。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：使用字体](../mfc/mfc-activex-controls-using-fonts.md)   
 [MFC ActiveX 控件：属性页](../mfc/mfc-activex-controls-property-pages.md)