---
title: "MFC ActiveX 控件：在 ActiveX 控件中使用数据绑定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bindable"
  - "requestedit"
  - "defaultbind"
  - "displaybind"
  - "dispid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "绑定控件 [C++], MFC ActiveX"
  - "控件 [MFC], 数据绑定"
  - "数据绑定 [C++], MFC ActiveX 控件"
  - "数据绑定控件 [C++], MFC ActiveX 控件"
  - "MFC ActiveX 控件, 数据绑定"
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：在 ActiveX 控件中使用数据绑定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 ActiveX 控件的更强大的功用之一是数据绑定，其允许控件属性与数据库中的特定字段绑定。  当用户修改此绑定属性的数据时，控件通知数据库和更新请求的记录字段。  之后数据库是成功还是失败的通知了请求控件。  
  
 本文包含任务的控件一侧。  实现与数据库交互的数据绑定是控件容器的责任。  您如何在容器中管理数据库交互超出了本文档的范围。  您如何准备数据绑定控件在本文的其余部分解释。  
  
 ![数据绑定控件的概念图](../mfc/media/vc374v1.png "vc374V1")  
数据绑定控件的概念图  
  
 `COleControl` 类提供两个成员函数简化了数据绑定的实现过程。  第一个函数，[BoundPropertyRequestEdit](../Topic/COleControl::BoundPropertyRequestEdit.md)，用于请求权限更改属性值。  在属性值成功更改后，第二个函数，[BoundPropertyChanged](../Topic/COleControl::BoundPropertyChanged.md) 被调用。  
  
 本文涵盖以下主题：  
  
-   [创建一个 Bindable Stock （备用）属性](#vchowcreatingbindablestockproperty)  
  
-   [创建 Bindable 的 get\/set 方法](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a> 创建一个 Bindable Stock （备用）属性  
 创建数据绑定的常用属性是可以的，尽管更可能的是您将想要选择 [bindable get\/set 方法](#vchowcreatingbindablegetsetmethod)。  
  
> [!NOTE]
>  默认情况下，常用属性具有 **bindable** 和 **requestedit** 特性。  
  
#### 使用"添加属性向导"，添加绑定属性  
  
1.  使用 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md) 开始项目。  
  
2.  右击控件的接口节点。  
  
     此操作打开快捷菜单。  
  
3.  从快捷菜单中，单击**“添加”**，然后单击**“添加属性”**。  
  
4.  从 **属性 名称** 下拉列表项选择一个实体。  例如，可以选择 **文本**。  
  
     由于 **文本** 是常用属性，**bindable** 和 **requestedit** 特性都已被检查了。  
  
5.  从 **IDL 特性** 选项卡上中选择下列复选框： **displaybind** 和 **defaultbind** 以便在项目的 .IDL 文件中为属性定义添加这些特性。  这些特性使控件向用户可见并使常用属性默认为绑定的属性。  
  
 此时，控件可以显示来自数据源的数据，但是，用户不能更新数据字段。  如果希望控件也可以更新数据，请更改 `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) 函数如下所示：  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 现在可以生成项目，将注册控件。  在在对话框中插入控件，**Data Field** 和 **Data Source （数据源）** 属性已添加，并且您可以选择一个数据源和字段在控件中显示。  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a> 创建 Bindable 的 get\/set 方法  
 除了数据绑定的 get\/set 方法之外，您也可以创建 [常用属性绑定](#vchowcreatingbindablestockproperty)  
  
> [!NOTE]
>  此过程假定您拥有一个 Windows 控件的子类 ActiveX 控件的项目。  
  
#### 使用"添加属性向导"，添加绑定的 get\/set 方法  
  
1.  加载控件项目。  
  
2.  在 **控件设置** 页中，选择将控件子类化的的窗口类。  例如，您可能想要子类化编辑控件。  
  
3.  加载控件项目。  
  
4.  右击控件的接口节点。  
  
     此操作打开快捷菜单。  
  
5.  从快捷菜单中，单击**“添加”**，然后单击**“添加属性”**。  
  
6.  在**“属性名称”**框中键入属性的名称。  对于此示例，使用 `MyProp`。  
  
7.  从**“属性类型”**下拉列表中选择数据类型。  对于此示例，使用 **short**。  
  
8.  对于 **Implementation Type**，单击 **Get\/Set Methods**。  
  
9. 从 IDL 特性选项卡上中选择下列复选框： **bindable**, **requestedit**，**displaybind**, 和 **defaultbind**以便在项目的 .IDL 文件中为属性定义添加这些特性。  这些特性使控件向用户可见并使常用属性默认为绑定的属性。  
  
10. 单击**“完成”**。  
  
11. 修改 `SetMyProp` 函数的主体，以便包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. 传递给 `BoundPropertyChanged` 和 `BoundPropertyRequestEdit` 函数的参数作为属性的调度标识符，其也是在 .idl 文件中传递给属性的 ID \(\) 特性的参数。  
  
13. 修改 [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) 函数，使其包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. 修改 `OnDraw` 函数，使其包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. 为控件类头文件的头文件的公用部分，为成员变量添加以下定义 \(构造函数\) ：  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. 使以下一行作为 `DoPropExchange` 函数的最后一行：  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. 修改 `OnResetState` 函数，使其包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. 修改 `GetMyProp` 函数，使其包含以下代码：  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 现在可以生成项目，将注册控件。  在在对话框中插入控件，**Data Field** 和 **Data Source （数据源）** 属性已添加，并且您可以选择一个数据源和字段在控件中显示。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [数据绑定控件（ADO 和 RDO）](../data/ado-rdo/data-bound-controls-ado-and-rdo.md)