---
title: MFC ActiveX 控件： 添加自定义方法 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cdf264bd0c2aa44bdeecc58b4bc8eb89c70fb91
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC ActiveX 控件：添加自定义方法
自定义方法不同于常用方法，因为它们并不已实现通过`COleControl`。 必须提供向控件添加的每个自定义方法的实现。  
  
 ActiveX 控件用户可以随时执行特定于控件的操作调用的自定义方法。 自定义方法的调度映射项的形式`DISP_FUNCTION`。  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a> 添加具有的自定义方法添加方法向导  
 下面的过程演示将 PtInCircle 自定义的方法添加到 ActiveX 控件的主干代码。 PtInCircle 确定传递到的控件的坐标为内部或外部圆。 此外可以使用此相同的过程添加其他自定义的方法。 替换你自定义方法的名称和其 PtInCircle 方法名称和参数的参数。  
  
> [!NOTE]
>  此示例使用`InCircle`事件的文章中的函数。 此函数的详细信息，请参阅文章[MFC ActiveX 控件： 向 ActiveX 控件添加自定义事件](../mfc/mfc-activex-controls-adding-custom-events.md)。  
  
#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>若要添加使用添加方法向导 PtInCircle 自定义方法  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中，单击**添加**，然后单击**添加方法**。  
  
     这将打开添加方法向导。  
  
5.  在**方法名称**框中，键入`PtInCircle`。  
  
6.  在**内部名称**框中，键入方法的内部函数的名称或使用默认值 (在这种情况下， `PtInCircle`)。  
  
7.  在**返回类型**框中，单击**VARIANT_BOOL**方法的返回类型。  
  
8.  使用**参数类型**和**参数名称**控件，则添加名为的参数`xCoord`(类型**OLE_XPOS_PIXELS**)。  
  
9. 使用**参数类型**和**参数名称**控件，则添加名为的参数`yCoord`(类型**OLE_YPOS_PIXELS**)。  
  
10. 单击 **“完成”**。  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a> 添加方法向导正在更改的自定义方法  
 当你添加自定义方法时，添加方法向导会对控件类标头进行一些更改 (。H） 和实现 (。CPP) 文件。 以下行添加到控件类标头中的调度映射声明 (。H） 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 此代码声明调度方法处理程序调用`PtInCircle`。 可以控制用户使用的外部名称 PtInCircle 调用此函数。  
  
 以下行添加到控件的。IDL 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 此行将 PtInCircle 方法分配一个特定的 ID 号，添加方法向导方法和属性列表中的方法的位置。 添加方法向导用于添加自定义方法，因为它的条目已自动添加到项目的。IDL 文件。  
  
 此外，以下行，位于实现 (。CPP) 文件中的控件类，已添加到控件的调度映射：  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 `DISP_FUNCTION`宏映射到控件的处理程序函数，该方法 PtInCircle `PtInCircle`，声明返回类型为**VARIANT_BOOL**，并声明类型的两个参数**VTS_XPOS_PIXELS**和**VTS_YPOSPIXELS**要传递给`PtInCircle`。  
  
 最后，添加方法向导添加存根 （stub） 函数`CSampleCtrl::PtInCircle`到底部的控件的实现 (。CPP) 文件。 有关`PtInCircle`能够按前面所述，必须能修改它，如下所示：  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [“类视图”和“对象浏览器”图标](/visualstudio/ide/class-view-and-object-browser-icons)

