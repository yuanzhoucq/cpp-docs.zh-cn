---
title: MFC ActiveX 控件：添加自定义方法
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: 88d486248eab5d980463764db34bf40b05b830dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364717"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC ActiveX 控件：添加自定义方法

自定义方法与库存方法不同，因为它们尚未由`COleControl`实现。 您必须为添加到控件中的每个自定义方法提供实现。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

ActiveX 控件用户可以随时调用自定义方法以执行特定于控件的操作。 自定义方法的调度映射条目为窗体DISP_FUNCTION。

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>使用添加方法向导添加自定义方法

下面的过程演示了将自定义方法 PtInCircle 添加到 ActiveX 控件的骨架代码中。 PtInCircle 确定传递给控件的坐标是圆内部还是外部。 此过程也可用于添加其他自定义方法。 将自定义方法名称及其参数替换为 PtInCircle 方法名称和参数。

> [!NOTE]
> 此示例使用文章"`InCircle`事件"中的函数。 有关此功能的详细信息，请参阅文章[MFC ActiveX 控件：将自定义事件添加到 ActiveX 控件](../mfc/mfc-activex-controls-adding-custom-events.md)。

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>使用添加方法向导添加 PtInCircle 自定义方法

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加方法**"。

   这将打开"添加方法向导"。

1. 在**方法名称**框中，键入*PtinCircle*。

1. 在 **"内部名称"** 框中，键入方法的内部函数的名称或使用默认值（本例中为*PtInCircle）。*

1. 在 **"返回类型"** 框中，单击方法返回类型的**VARIANT_BOOL。**

1. 使用**参数类型**和**参数名称**控件，添加名为*xCoord*的参数 *（OLE_XPOS_PIXELS*类型）。

1. 使用**参数类型**和**参数名称**控件，添加名为*yCoord*的参数（类型*OLE_YPOS_PIXELS*）。

1. 单击“完成”  。

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>为自定义方法添加方法向导更改

添加自定义方法时，添加方法向导会对控件类标头 （.H） 和实施 （.CPP）文件。 以下行将添加到控件类标头 （中）中的调度映射声明 （。H） 文件：

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

此代码声明一个称为`PtInCircle`的调度方法处理程序。 控件用户可以使用外部名称`PtInCircle`调用此功能。

以下行将添加到控件的 。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

此行为`PtInCircle`方法分配特定的 ID 号、该方法在"添加方法向导"方法和属性列表中的位置。 由于 Add 方法向导用于添加自定义方法，因此其条目将自动添加到项目的 。IDL 文件。

此外，以下行，位于实现 （。控制类的CPP）文件，被添加到控件的调度映射中：

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

DISP_FUNCTION宏`PtInCircle`将该方法映射到控件的处理程序函数 ，`PtInCircle`声明返回类型为**VARIANT_BOOL，** 并声明要传递给`PtInCircle`的**VTS_XPOS_PIXELS****和VTS_YPOSPIXELS**的两个参数。

最后，添加方法向导将存根函数`CSampleCtrl::PtInCircle`添加到控件的实现的底部 （。CPP）文件。 要`PtInCircle`按照前面所述运行，必须修改如下：

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[类视图和对象浏览器图标](/visualstudio/ide/class-view-and-object-browser-icons)
