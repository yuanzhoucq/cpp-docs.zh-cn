---
title: 添加属性页（ATL 教程，第 6 部分）
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
ms.openlocfilehash: 467ae19c372e24b2d368002cb83367b7087136fd
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078771"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>添加属性页（ATL 教程，第 6 部分）

> [!NOTE]
> ATL OLE DB 提供程序向导不适用于 Visual Studio 2019 及更高版本。

属性页实现为各个 COM 对象，这样就能在需要时共享了。 在这一步中，你将执行以下任务来将属性页添加到控件中：

- 创建属性页资源

- 添加用于创建和管理属性页的代码

- 将属性页添加到控件中

## <a name="creating-the-property-page-resource"></a>创建属性页资源

若要将属性页添加到控件中，请使用 ATL 属性页模板。

### <a name="to-add-a-property-page"></a>添加属性页的具体步骤

1. 在“解决方案资源管理器”中，右键单击“`Polygon`”。

1. 在快捷菜单中，依次单击“添加” > “新项”。

1. 在模板列表中，依次选择“ATL” > “ATL 属性页”，再单击“添加”。

1. 当“ATL 属性页向导”显示时，在“短名称”中输入“PolyProp”。

1. 单击“字符串”以打开“字符串”页，并在“标题”中输入“&Polygon”。

   属性页的“标题”是在属性页的选项卡中显示的字符串。 “文档字符串”是属性框架用来置于状态栏或工具提示中的说明。 请注意，标准属性框架暂不使用此字符串，因此可以保留使用默认内容。 暂不会生成“帮助文件”，所以请删除此文本框中的条目。

1. 单击“完成”。此时，系统创建属性页对象。

系统创建以下三个文件：

|文件|说明|
|----------|-----------------|
|PolyProp.h|包含实现属性页的 C++ 类 `CPolyProp`。|
|PolyProp.cpp|包含 PolyProp.h 文件。|
|PolyProp.rgs|注册属性页对象的注册表脚本。|

还进行了以下代码更改：

- 将新属性页添加到 Polygon.cpp 中的对象条目映射内。

- 将 `PolyProp` 类添加到 polygon.idl 文件中。

- 将新注册表脚本文件 PolyProp.rgs 添加到项目资源中。

- 将对话框模板添加到属性页的项目资源中。

- 将你指定的属性字符串添加到资源字符串表中。

现在，添加要在属性页上显示的字段。

### <a name="to-add-fields-to-the-property-page"></a>将字段添加到属性页的具体步骤

1. 在“解决方案资源管理器”中，双击 Polygon.rc 资源文件。 这会打开“资源视图”。

1. 在“资源视图”中，展开“`Dialog`”节点并双击“`IDD_POLYPROP`”。 请注意，随即显示的对话框是空的，只有一个指示你在此处插入控件的标签。

1. 选择此标签，然后通过更改“属性”`Sides:`**窗口中的“描述文字”** **文本，将标签更改为显示“** ”。

1. 调整标签框的大小，让它适应文本大小。

1. 将“工具箱”中的“编辑控件”拖到标签的右侧。

1. 最后，使用“属性”窗口，将编辑控件的“ID”`IDC_SIDES`**更改为“** ”。

这就完成了属性页资源的创建流程。

## <a name="adding-code-to-create-and-manage-the-property-page"></a>添加用于创建和管理属性页的代码

至此，已创建属性页资源。需要编写实现代码了。

首先，将 `CPolyProp` 类启用为，在用户按下“应用”按钮后，设置对象边数。

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>将 Apply 函数修改为设置边数的具体步骤

1. 将 PolyProp.h 中的 `Apply` 函数替换为下面的代码：

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

属性页一次可以附加有多个客户端，因此 `Apply` 函数循环并对包含从编辑框检索到的值的每个客户端调用 `put_Sides`。 你使用的是 [CComQIPtr](../atl/reference/ccomqiptr-class.md) 类，它对每个对象执行 `QueryInterface`，以从 `IPolyCtl` 接口获取 `IUnknown` 接口（存储在 `m_ppUnk` 数组中）。

现在，代码检查能否正常设置 `Sides` 属性。 如果失败，代码显示一个消息框，其中显示来自 `IErrorInfo` 接口的错误详细信息。 通常情况下，容器会先向对象请求获取 `ISupportErrorInfo` 接口并调用 `InterfaceSupportsErrorInfo`，以确定对象是否支持设置错误信息。 可以跳过此任务。

[CComPtr](../atl/reference/ccomptr-class.md) 有助于自动处理引用计数，因此无需对接口调用 `Release`。 `CComBSTR` 有助于执行 BSTR 处理，因此无需执行最后的 `SysFreeString` 调用。 你还使用各种字符串转换类之一，所以可以根据需要转换 BSTR（正因为此，USES_CONVERSION 宏位于函数开头处）。

此外，还需要设置属性页的脏标志来指明应启用“应用”按钮。 这发生在用户更改“边数”编辑框中的值时。

### <a name="to-handle-the-apply-button"></a>处理“应用”按钮的具体步骤

1. 在“类视图”中，右键单击“`CPolyProp`”，再单击快捷菜单中的“属性”。

1. 在“属性”窗口中，单击“事件”图标。

1. 在事件列表中，展开“`IDC_SIDES`”节点。

1. 选择“`EN_CHANGE`”，然后在右侧的下拉菜单中，单击“**添加> OnEnChangeSides”\<** 。 此时，`OnEnChangeSides` 处理程序声明会添加到 Polyprop.h 中，并且处理程序实现会添加到 Polyprop.cpp 中。

接下来，修改处理程序。

### <a name="to-modify-the-onenchangesides-method"></a>修改 OnEnChangeSides 方法的具体步骤

1. 将 Polyprop.cpp 中的以下代码添加到 `OnEnChangeSides` 方法（删除向导在其中放置的任何代码）：

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

当 `OnEnChangeSides` 消息与 `WM_COMMAND` 控件的 `EN_CHANGE` 通知一起发送时，便会调用 `IDC_SIDES`。 然后，`OnEnChangeSides` 调用 `SetDirty` 并传递 TRUE，以指明属性页现在为脏，并且应启用“应用”按钮。

## <a name="adding-the-property-page-to-the-control"></a>将属性页添加到控件中

ATL 属性页模板和向导不会自动为你将属性页添加到控件中，因为项目中可能有多个控件。 你需要将条目添加到控件的属性映射中。

### <a name="to-add-the-property-page"></a>添加属性页的具体步骤

1. 打开 PolyCtl.h，并将下面这些代码行添加到属性映射中：

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

控件的属性映射现在如下所示：

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

你本可以添加包含属性页 CLSID 的 `PROP_PAGE` 宏，但如果使用所示的 `PROP_ENTRY` 宏，`Sides` 属性值也会随控件一起保存。

宏的三个参数分别是属性说明、属性的 DISPID 和属性所在属性页的 CLSID。 例如，将控件加载到 Visual Basic 并在设计时设置边数时，就会发现这非常有用。 因为边数已保存，所以在你重新加载 Visual Basic 项目时，边数会还原。

## <a name="building-and-testing-the-control"></a>生成和测试控件

现在，生成相应控件，并将它插入 ActiveX 控件测试容器中。 在“测试容器”中，单击“编辑”菜单上的“PolyCtl 类对象”。 此时，属性页显示，其中包含你添加的信息。

“应用”按钮最初处于禁用状态。 首先，在“边数”框中键入值。此时，“应用”按钮变为启用状态。 输入完值后，单击“应用”按钮。 此时，控件显示更改，且“应用”按钮再次处于禁用状态。 尝试输入无效值。 你会看到一个消息框，其中包含通过 `put_Sides` 函数设置的错误说明。

接下来，将在网页上添加控件。

[返回到第 5 步](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [转到第 7 步](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>另请参阅

[教程](../atl/active-template-library-atl-tutorial.md)
