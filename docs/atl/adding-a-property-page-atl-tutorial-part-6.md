---
title: 添加属性页 (ATL 教程，第 6) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: get-started-article
dev_langs:
- C++
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 067c5d662fee3838a33a3b53fd5dab2946ab50cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>添加属性页（ATL 教程，第 6 部分）
属性页是作为单独的 COM 对象，允许它们在需要时共享实现的。 在此步骤中，您将执行以下任务以添加到控件的属性页：  
  
-   创建属性页资源  
  
-   添加代码以创建和管理的属性页  
  
-   向控件添加的属性页  
  
## <a name="creating-the-property-page-resource"></a>创建属性页资源  
 若要向控件中添加属性页，使用 ATL 添加类向导。  
  
#### <a name="to-add-a-property-page"></a>要添加属性页  
  
1.  在解决方案资源管理器，右键单击多边形。  
  
2.  在快捷菜单上，单击**添加**，然后单击**添加类**。  
  
3.  从模板列表中，选择**ATL 属性页**单击**添加**。  
  
4.  ATL 属性页向导出现时，输入`PolyProp`作为**短**名称。  
  
5.  单击**字符串**以打开**字符串**页上，然后输入**& 多边形**作为**标题**。  
  
     **标题**的属性页是显示在该页面的选项卡的字符串。 **文档字符串**是属性框架使用放入状态行或工具提示中的说明。 请注意，标准属性框架当前不使用此字符串中，因此你可以将它保留为默认内容。 你将不会生成**帮助文件**目前，因此请删除该文本框中的条目。  
  
6.  单击**完成**，将创建的属性页对象。  
  
 创建以下三个文件：  
  
|文件|描述|  
|----------|-----------------|  
|PolyProp.h|包含 c + + 类`CPolyProp`，它实现的属性页。|  
|PolyProp.cpp|包括 PolyProp.h 文件。|  
|PolyProp.rgs|注册表脚本注册的属性页对象。|  
  
 此外进行了以下的代码更改：  
  
-   新的属性页添加到 Polygon.cpp 中的对象项映射。  
  
-   `PolyProp`类添加到 Polygon.idl 文件。  
  
-   新的注册表脚本文件 PolyProp.rgs 添加到项目资源。  
  
-   对话框模板添加到属性页的项目资源。  
  
-   你指定的属性字符串添加到资源字符串表中。  
  
 现在，添加你想要在属性页上显示的字段。  
  
#### <a name="to-add-fields-to-the-property-page"></a>将字段添加到属性页  
  
1.  在解决方案资源管理器中，双击 Polygon.rc 资源文件。 这将打开资源视图。  
  
2.  在资源视图中，展开对话框节点，然后双击 IDD_POLYPROP。 请注意显示的对话框中为空除外，告诉你在此处插入控件的标签。  
  
3.  选择该标签并将其更改为读取`Sides:`通过更改**标题**中文**属性**窗口。  
  
4.  调整大小标签框中，以便它非常适合的文本大小。  
  
5.  将编辑控件从工具箱拖到标签的右侧。  
  
6.  最后，更改**ID**编辑控件的`IDC_SIDES`使用属性窗口。  
  
 这将完成创建属性页资源的过程。  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>添加代码以创建和管理的属性页  
 既然你已经创建属性页资源，你需要编写的实现代码。  
  
 首先，启用`CPolyProp`类在你的对象中设置的边数时**应用**按下按钮。  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>若要修改应用函数以设置的边数  
  
1.  替换`Apply`中 PolyProp.h 函数替换为以下代码：  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 属性页中可以有多个客户端连接到它一次，因此`Apply`函数循环，调用`put_Sides`从编辑框中检索值的每个客户端。 你使用[CComQIPtr](../atl/reference/ccomqiptr-class.md)类，后者将执行`QueryInterface`要获取每个对象`IPolyCtl`接口从**IUnknown**接口 (存储在`m_ppUnk`数组)。  
  
 现在，代码检查该设置`Sides`实际工作的属性。 如果失败，代码将显示一个消息框，显示错误详细信息从**IErrorInfo**接口。 通常，容器请求的对象**ISupportErrorInfo**接口并调用`InterfaceSupportsErrorInfo`第一个，以确定对象是否支持设置错误信息。 你可以跳过此任务。  
  
 [CComPtr](../atl/reference/ccomptr-class.md)可帮助你通过自动处理引用计数，因此不需要调用`Release`接口上。 `CComBSTR`可帮助你与`BSTR`处理，因此不需要执行最终`SysFreeString`调用。 你还使用一个不同的字符串转换类，以便可以转换`BSTR`如有必要 (正因如此`USES_CONVERSION`宏位于函数的开始)。  
  
 你还需要设置属性页的已更新标志以指示**应用**应启用按钮。 发生这种情况是当用户更改中的值**边**编辑框。  
  
#### <a name="to-handle-the-apply-button"></a>若要处理应用按钮  
  
1.  在类视图中，右键单击 CPolyProp，然后单击**属性**快捷菜单上。  
  
2.  在属性窗口中，单击**事件**图标。  
  
3.  展开`IDC_SIDES`节点在事件列表中。  
  
4.  选择`EN_CHANGE`，然后从右侧的下拉列表菜单，单击**\<添加 > OnEnChangeSides**。 `OnEnChangeSides`处理程序声明将添加到 Polyprop.h 和到 Polyprop.cpp 的处理程序实现。  
  
 接下来，您将修改该处理程序。  
  
#### <a name="to-modify-the-onenchangesides-method"></a>若要修改的 OnEnChangeSides 方法  
  
1.  将以下代码添加到 Polyprop.cpp 中`OnEnChangeSides`（删除向导放置在那里的任何代码） 的方法：  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides`时将会调用**WM_COMMAND**消息不会发送**EN_CHANGE**通知`IDC_SIDES`控件。 `OnEnChangeSides`然后调用`SetDirty`并将传递`TRUE`以指示该属性页现在是脏和**应用**应启用按钮。  
  
## <a name="adding-the-property-page-to-the-control"></a>向控件添加的属性页  
 ATL 添加类向导和 ATL 属性页向导不属性页控件为你将自动添加到，因为你的项目中可能有多个控件。 你将需要将条目添加到控件的属性映射。  
  
#### <a name="to-add-the-property-page"></a>若要添加的属性页  
  
1.  打开 PolyCtl.h 并将以下行添加到属性映射：  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 控件的属性映射现在如下所示：  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 无法添加`PROP_PAGE`通过属性页，但如果你将 CLSID 宏`PROP_ENTRY`宏如所示，`Sides`保存该控件时，也将保存属性值。  
  
 该宏的三个参数是属性说明，该属性的 DISPID 和对其具有属性的属性页的 CLSID。 如果加载到 Visual Basic 控件和在设计时设置的边数等，这非常有用。 由于保存的边数，在重新加载 Visual Basic 项目时，将还原的边数。  
  
## <a name="building-and-testing-the-control"></a>生成和测试控件  
 现在，生成该控件并将其插入到 ActiveX 控件测试容器。 在测试容器中，在**编辑**菜单上，单击**PolyCtl 类对象**。 属性页出现后;单击**多边形**选项卡。  
  
 **应用**按钮最初处于禁用状态。 开始键入中的值**边**框和**应用**按钮将变成启用状态。 输入的值之后，请单击**应用**按钮。 控件显示更改，与**应用**按钮再次禁用。 请尝试输入无效值。 你将看到一个包含你设置从错误描述消息框`put_Sides`函数。  
  
 接下来，你会将您在网页上的控件。  
  
 [返回到步骤 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124;[到步骤 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)

