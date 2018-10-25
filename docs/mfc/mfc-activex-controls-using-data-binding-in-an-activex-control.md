---
title: MFC ActiveX 控件： 在 ActiveX 控件中使用数据绑定 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: 397356f8144e3680f3b2d19824d19c0a3bbaddd1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062608"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX 控件：在 ActiveX 控件中使用数据绑定

ActiveX 控件的功能更强大的用途之一是数据绑定，它允许控件绑定在一起在数据库中的特定字段的属性。 当用户修改此绑定的属性中的数据时，该控件通知数据库和更新记录的字段的请求。 控制的成功或失败的请求，然后会通知数据库。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

本文介绍了您的任务在控件方面。 实现与数据库交互的数据绑定负责控制容器。 如何在容器中管理数据库交互已超出本文档讨论范围。 本文的其余部分介绍如何准备用于数据绑定控件。

![数据的概念图&#45;绑定控件](../mfc/media/vc374v1.gif "vc374v1")的数据绑定控件的概念图

`COleControl`类提供了两个成员函数，使数据绑定实现简单的过程。 第一个函数[BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit)，用于请求更改的属性值的权限。 [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged)，第二个函数，称为已成功更改属性值之后。

本文介绍了以下主题：

- [创建一个可绑定的常用属性](#vchowcreatingbindablestockproperty)

- [创建可绑定的 Get/Set 方法](#vchowcreatingbindablegetsetmethod)

##  <a name="vchowcreatingbindablestockproperty"></a> 创建一个可绑定的常用属性

它是可以创建一个数据绑定的常用属性，尽管很有可能，你将想[可绑定的 get/set 方法](#vchowcreatingbindablegetsetmethod)。

> [!NOTE]
>  常用属性具有`bindable`和`requestedit`属性默认情况下。

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>若要添加一个可绑定的常用属性，使用添加属性向导

1. 开始项目使用[MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)。

1. 右键单击您的控件的接口节点。

   这将打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加属性**。

1. 选择一个从条目**属性名称**下拉列表。 例如，可以选择**文本**。

   因为**文本**一个常用属性**可绑定**并**requestedit**属性已选中。

1. 选中以下复选框从**IDL 特性**选项卡： **displaybind**并**defaultbind**将属性添加到项目的属性定义。IDL 文件。 这些属性使控件对用户可见，并使常用属性的默认可绑定属性。

此时，您的控件可以显示来自数据源，但用户将无法再更新数据字段。 如果您希望控件还可以更新数据时，更改`OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函数能够查询，如下所示：

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

现在可以生成项目，将注册该控件。 当您在对话框中，插入控件**数据字段**并**数据源**属性将已添加并且你现在可以选择数据源和要在控件中显示字段。

##  <a name="vchowcreatingbindablegetsetmethod"></a> 创建可绑定的 Get/Set 方法

除了数据绑定 get/set 方法，还可以创建[股票的可绑定属性](#vchowcreatingbindablestockproperty)。

> [!NOTE]
>  此过程假定你具有 ActiveX 控件项目的 Windows 控件的子类。

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>若要添加使用添加属性向导的可绑定的 get/set 方法

1. 加载控件的项目。

1. 上**控制设置**页上，选择为子类的控件的窗口类。 例如，您可以为子类的编辑控件。

1. 加载控件的项目。

1. 右键单击您的控件的接口节点。

   这将打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加属性**。

1. 键入中的属性名称**属性名称**框。 使用`MyProp`对于此示例。

1. 选择数据类型从**属性类型**下拉列表框。 使用**短**对于此示例。

1. 对于“实现类型” ，请单击“Get/Set 方法” 。

9. 从 IDL 特性选项卡中选择以下复选框：**可绑定**， **requestedit**， **displaybind**，以及**defaultbind**添加到属性定义在项目的属性。IDL 文件。 这些属性使控件对用户可见，并使常用属性的默认可绑定属性。

10. 单击 **“完成”**。

11. 修改的正文`SetMyProp`函数，使其包含以下代码：

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

12. 将参数传递给`BoundPropertyChanged`和`BoundPropertyRequestEdit`函数是属性，它是传递给 id （） 属性中的属性的参数的 dispid。IDL 文件。

13. 修改[OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函数，它包含以下代码：

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

14. 修改`OnDraw`函数，使其包含以下代码：

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

15. 标头文件的头文件的控件类的公共部分，添加以下定义 （构造函数） 的成员变量：

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

16. 使以下行中的最后一行`DoPropExchange`函数：

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

17. 修改`OnResetState`函数，使其包含以下代码：

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

18. 修改`GetMyProp`函数，使其包含以下代码：

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

现在可以生成项目，将注册该控件。 当您在对话框中，插入控件**数据字段**并**数据源**属性将已添加并且你现在可以选择数据源和要在控件中显示字段。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

