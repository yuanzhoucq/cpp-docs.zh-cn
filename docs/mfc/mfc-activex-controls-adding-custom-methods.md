---
title: MFC ActiveX 控件：添加自定义方法
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: e32a1c372d89fc4ade414b20a0f77fa162807250
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626160"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC ActiveX 控件：添加自定义方法

自定义方法与 stock 方法的不同之处在于，它们尚未由实现 `COleControl` 。 必须提供添加到控件的每个自定义方法的实现。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

ActiveX 控件用户可随时调用自定义方法来执行特定于控件的操作。 自定义方法的调度映射项的格式为 DISP_FUNCTION。

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>使用 "添加方法向导" 添加自定义方法

下面的过程演示如何将自定义方法 PtInCircle 添加到 ActiveX 控件的主干代码。 PtInCircle 确定传递到控件的坐标是位于圆圈内部还是外部。 此过程也可用于添加其他自定义方法。 将自定义方法名称和参数替换为 PtInCircle 方法名称和参数。

> [!NOTE]
> 此示例使用 `InCircle` 项目事件中的函数。 有关此函数的详细信息，请参阅[MFC Activex 控件：向 ActiveX 控件添加自定义事件](mfc-activex-controls-adding-custom-events.md)一文。

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>使用添加方法向导添加 PtInCircle 自定义方法

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加方法**"。

   这将打开 "添加方法向导"。

1. 在 "**方法名称**" 框中，键入*PtInCircle*。

1. 在 "**内部名称**" 框中，键入方法的内部函数的名称，或使用默认值（在本例中为*PtInCircle*）。

1. 在 "**返回类型**" 框中，单击该方法的返回类型**VARIANT_BOOL** 。

1. 使用**参数类型**和**参数名称**控件添加名为*xCoord*的参数（类型*OLE_XPOS_PIXELS*）。

1. 使用**参数类型**和**参数名称**控件添加名为*yCoord*的参数（类型*OLE_YPOS_PIXELS*）。

1. 单击“完成”。

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>自定义方法的添加方法向导更改

添加自定义方法时，添加方法向导会对控件类标头进行一些更改（。H）和实现（。CPP）文件。 将以下行添加到控件类标头中的调度映射声明（。H）文件：

[!code-cpp[NVC_MFC_AxUI#18](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

此代码声明了一个名为的调度方法处理程序 `PtInCircle` 。 此函数可以由控件用户使用外部名称调用 `PtInCircle` 。

以下行将添加到控件的。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#19](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

此行将方法指定 `PtInCircle` 为特定 ID 号，方法在 "添加方法向导" 的 "方法和属性" 列表中的位置。 由于添加方法向导用于添加自定义方法，因此它的项自动添加到项目的。IDL 文件。

此外，还会在实现（。CPP）文件，将添加到控件的调度映射：

[!code-cpp[NVC_MFC_AxUI#20](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

DISP_FUNCTION 宏会将方法映射 `PtInCircle` 到控件的处理程序函数， `PtInCircle` 声明要**VARIANT_BOOL**的返回类型，并声明要传递到**VTS_XPOS_PIXELS**和**VTS_YPOSPIXELS**类型的两个参数 `PtInCircle` 。

最后，添加方法向导将存根函数添加 `CSampleCtrl::PtInCircle` 到控件实现的底部（。CPP）文件。 `PtInCircle`要使正常工作，必须按如下所述修改它：

[!code-cpp[NVC_MFC_AxUI#21](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[类视图和对象浏览器图标](/visualstudio/ide/class-view-and-object-browser-icons)
