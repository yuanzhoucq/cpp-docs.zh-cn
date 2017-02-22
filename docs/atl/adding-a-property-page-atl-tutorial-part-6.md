---
title: "添加属性页（ATL 教程，第 6 部分） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 添加属性页（ATL 教程，第 6 部分）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

属性页实现为单独的COM对象，从而使它们如果需要共享。  在此步骤中，您将执行以下任务来添加属性页到控件:  
  
-   创建属性页资源  
  
-   添加代码以创建和管理属性页  
  
-   添加属性页到控件  
  
## 创建属性页资源  
 若要添加属性页到控件，请使用ATL添加选件类向导。  
  
#### 添加属性页  
  
1.  在解决方案资源管理器中，右击多边形。  
  
2.  在快捷菜单上，单击“添加”，然后单击“添加类”。  
  
3.  从模板、选择 **ATL属性页** 然后单击 **添加**列表。  
  
4.  当ATL属性页向导后，输入 `PolyProp` 作为 **short** 名称。  
  
5.  单击 **字符串** 打开 **字符串** 页并进入 **&Polygon** 作为 **前缀**。  
  
     属性页的 **前缀** 会出现在该页的选项卡的字符串。  **文档字符串** 是属性框架在状态行或工具提示使用中的说明。  请注意标准属性框架当前不使用此字符串，因此，可以将其保留为默认内容。  当时不会生成 **帮助文件**，因此，请移除该文本框的项。  
  
6.  单击 **完成**，因此，属性页将会创建对象。  
  
 下列三个文件创建的:  
  
|文件|说明|  
|--------|--------|  
|PolyProp.h|包含C\+\+选件类 `CPolyProp`，实现属性页。|  
|PolyProp.cpp|包括PolyProp.h文件。|  
|PolyProp.rgs|该注册表的脚本注册属性页对象。|  
  
 以下代码更改也组成:  
  
-   新的属性页中添加到Polygon.cpp的对象项映射。  
  
-   `PolyProp` 选件类添加到Polygon.idl文件。  
  
-   新的注册表脚本文件PolyProp.rgs添加到项目资源。  
  
-   对话框模板添加到属性页的项目资源。  
  
-   您指定的属性字符串添加到资源字符串表。  
  
 现在添加字段要显示在属性页。  
  
#### 将字段添加到属性页  
  
1.  在解决方案资源管理器中，双击Polygon.rc资源文件。  这将打开资源视图。  
  
2.  在"资源视图"中，展开对话框节点并双击IDD\_POLYPROP。  注意显示的对话框为空\(告诉您插入您的控件在此处的标签。  
  
3.  选择该标签并更改它通过修改在 **属性** 窗口的 **声明** 文本 `端:`。  
  
4.  调整标签框，使其适合文本的大小。  
  
5.  在标签的右侧从工具箱拖动的编辑控件。  
  
6.  最后，使用"属性"窗口中，将编辑控件的 **ID** 到 `IDC_SIDES`。  
  
 这是创建属性页资源处理。  
  
## 添加代码以创建和管理属性页  
 您已经创建了属性页资源，需要编写实现代码。  
  
 首先，那么，当 **适用** 按钮时，请使 `CPolyProp` 选件类设置边数在对象的。  
  
#### 若要修改应用请函数设置边数  
  
1.  用下面的代码替换该PolyProp.h的 `Apply` 功能:  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 属性页可以包含多个客户端每个附加到它，因此，`Apply` 函数循环并对每个客户端的 `put_Sides` 具有从编辑框中检索的值的。  使用 [CComQIPtr](../atl/reference/ccomqiptr-class.md) 选件类，以针对每个对象的 `QueryInterface` 从 **IUnknown** 接口的 `IPolyCtl` 接口\(存储在 `m_ppUnk` 数组）。  
  
 现在代码检查设置 `Sides` 属性的实际工作。  如果它失败，代码显示了从 **IErrorInfo** 接口的消息框错误详细信息。  通常，容器请求对象 **ISupportErrorInfo** 接口并将调用 `InterfaceSupportsErrorInfo`，确定对象是否支持将错误信息。  可以跳过此任务。  
  
 [CComPtr](../atl/reference/ccomptr-class.md) 通过自动处理计数的引用帮助您，因此，您不需要调用接口中的 `Release`。  `CComBSTR` 帮助您 `BSTR` 的处理，因此，您不必执行最终 `SysFreeString` 调用。  也可以使用之一执行各种字符串转换选件类，因此，如果必要，可以转换 `BSTR` \(所以 `USES_CONVERSION` 宏是在函数的开始）。  
  
 您还需要设置属性页的错误的标志指示应启用 **适用** 按钮。  当用户更改在 **端** 的值编辑框，则会出现此错误。  
  
#### 处理应用按钮  
  
1.  在选件类视图中，右击CPolyProp然后单击 **属性** 在快捷菜单上。  
  
2.  在"属性"窗口中，单击 **事件** 图标。  
  
3.  展开事件的 `IDC_SIDES` 节点列表。  
  
4.  选择的 `EN_CHANGE`，然后从下拉菜单在右侧，单击 **\<Add\> OnEnChangeSides**。  `OnEnChangeSides` 处理程序声明将添加到Polyprop.h和处理程序实现。Polyprop.cpp。  
  
 接下来，您将修改处理程序。  
  
#### 修改OnEnChangeSides方法  
  
1.  将Polyprop.cpp的以下代码添加到 `OnEnChangeSides` 方法\(删除任何代码向导将其中\):  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 当 **WM\_COMMAND** 发送与 `IDC_SIDES` 控件，的 **EN\_CHANGE** 通知`OnEnChangeSides` 将调用。  `OnEnChangeSides` 然后调用 `SetDirty`，并将指示属性页的 `TRUE` 现在有错误，并且应启用 **适用** 按钮。  
  
## 添加属性页到控件  
 ATL添加选件类向导，并ATL属性页向导不会自动添加属性页添加到您的控件，因为可以项目中有多个控件。  您需要将项添加到控件的属性映射。  
  
#### 添加属性页  
  
1.  打开PolyCtl.h并将此行。属性映射:  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 控件的属性映射现在如下所示:  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/CPP/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 可以增加了您的属性页CLSID的一 `PROP_PAGE` 宏，但是，如果您使用 `PROP_ENTRY` 宏所示，`Sides` 属性值还保存，当控件保存时。  
  
 对宏的三个参数是属性声明、属性的DISPID和具有此操作的属性页的CLSID。  这是有用的，则，例如，则填充控件。Visual Basic并设置边数在设计时。  由于边数保存，那么，当您重新加载Visual Basic项目，将还原边数。  
  
## 生成并测试控件  
 现在将生成控件并粘贴到中的ActiveX控件测试容器。  在测试容器中，在 **编辑** 菜单上，单击 **PolyCtl选件类对象**。  属性页;单击 **多边形** 选项。  
  
 **适用** 按钮最初禁用。  开始键入在 **端** 框中的值，并 **适用** 按钮将变为启用。  在完成输入值后，单击 **适用** 按钮。  控件显示更改和 **适用** 按钮再次被禁用。  输入无效的值的尝试。  您将看到消息框包含该错误说明您从 `put_Sides` 功能集。  
  
 接下来，在网页中放置到的控件。  
  
 [返回第5步](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [在到步骤7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## 请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)