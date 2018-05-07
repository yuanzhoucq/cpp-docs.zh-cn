---
title: MFC ActiveX 控件： 在 ActiveX 控件中使用数据绑定 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab5195cc2381e515688182ad73452b07afd06b98
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX 控件：在 ActiveX 控件中使用数据绑定
ActiveX 控件的功能更强大用途之一是允许要绑定在一起在数据库中的特定字段的控件属性的数据绑定。 当用户修改了此绑定的属性中的数据时，该控件通知的数据库和请求将更新记录的字段。 控制的成功或失败的请求，然后会通知数据库。  
  
 本文介绍如何控制一端你的任务。 实现与数据库的数据绑定交互负责的控件容器。 你如何管理容器中的数据库交互不在本文档的范围。 本文的其余部分中描述了如何准备用于数据绑定控件。  
  
 ![数据的概念图&#45;绑定控件](../mfc/media/vc374v1.gif "vc374v1")  
数据绑定控件的概念图  
  
 `COleControl`类提供了两个成员函数，用于使数据绑定来实现一个简单的过程。 第一个函数， [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit)，用来请求更改的属性值的权限。 [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged)，第二个函数中，称为后成功更改属性值。  
  
 本文介绍了以下主题：  
  
-   [创建可绑定的常用属性](#vchowcreatingbindablestockproperty)  
  
-   [创建可绑定的 Get/Set 方法](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a> 创建可绑定的常用属性  
 它是可以创建数据绑定的常用属性的但它是更有可能，你将希望[可绑定的 get/set 方法](#vchowcreatingbindablegetsetmethod)。  
  
> [!NOTE]
>  常用属性具有**可绑定**和**requestedit**默认情况下的属性。  
  
#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>若要添加使用添加属性向导的可绑定常用属性  
  
1.  开始项目使用[MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)。  
  
2.  右键单击你的控件的接口节点。  
  
     这将打开快捷菜单。  
  
3.  从快捷菜单中，单击**添加**，然后单击**添加属性**。  
  
4.  选择一个项**属性名称**下拉列表。 例如，你可以选择**文本**。  
  
     因为**文本**是常用的属性，**可绑定**和**requestedit**已检查属性。  
  
5.  选中以下复选框**IDL 特性**选项卡： **displaybind**和**defaultbind**将属性添加到在项目的属性定义。IDL 文件。 这些特性使控件对用户可见，请常用属性的默认可绑定属性。  
  
 此时，你的控件可以显示来自数据源的数据，但用户将无法更新数据字段。 如果您希望控件还可以更新数据时，更改`OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函数看起来，如下所示：  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 你现在可以生成项目，将注册控件。 当在对话框中，插入控件**数据字段**和**数据源**属性将已添加且你现在可以选择数据源，并在控件中显示的字段。  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a> 创建可绑定的 Get/Set 方法  
 除了数据绑定 get/set 方法，还可以创建[可绑定的常用属性](#vchowcreatingbindablestockproperty)。  
  
> [!NOTE]
>  此过程假定你具有 ActiveX 控件项目的 Windows 控件的子类。  
  
#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>若要添加使用添加属性向导可绑定的 get/set 方法  
  
1.  加载控件的项目。  
  
2.  上**控制设置**页上，选择子类化控件的窗口类。 例如，您可能子类化希望编辑控件。  
  
3.  加载控件的项目。  
  
4.  右键单击你的控件的接口节点。  
  
     这将打开快捷菜单。  
  
5.  从快捷菜单中，单击**添加**，然后单击**添加属性**。  
  
6.  键入中的属性名称**属性名称**框。 使用`MyProp`对于此示例。  
  
7.  选择数据类型从**属性类型**下拉列表框。 使用**短**对于此示例。  
  
8.  对于“实现类型” ，请单击“Get/Set 方法” 。  
  
9. 从 IDL 特性选项卡中选择以下的复选框：**可绑定**， **requestedit**， **displaybind**，和**defaultbind**添加到属性定义在项目的属性。IDL 文件。 这些特性使控件对用户可见，请常用属性的默认可绑定属性。  
  
10. 单击 **“完成”**。  
  
11. 修改的正文`SetMyProp`函数，以便它包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. 参数传递给`BoundPropertyChanged`和`BoundPropertyRequestEdit`函数是属性，它是传递给 id （） 属性中为属性的参数的 dispid。IDL 文件。  
  
13. 修改[OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函数使其包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. 修改`OnDraw`函数，以便它包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. 到你的控件类的头文件的标头文件的公共部分，添加以下定义 （构造函数） 的成员变量：  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. 将以下行中的最后一行`DoPropExchange`函数：  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. 修改`OnResetState`函数，以便它包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. 修改`GetMyProp`函数，以便它包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 你现在可以生成项目，将注册控件。 当在对话框中，插入控件**数据字段**和**数据源**属性将已添加且你现在可以选择数据源，并在控件中显示的字段。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   

