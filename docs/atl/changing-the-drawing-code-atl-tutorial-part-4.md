---
title: 更改绘图代码 (ATL 教程，第 4) |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c077aca8c3276fac963eda8cdd2c413a9d6d5f5b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358907"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>更改绘图代码（ATL 教程，第 4 部分）
默认情况下，控件的绘制代码显示的文本和正方形**PolyCtl**。 在此步骤中，你将更改要显示一些更有趣的内容的代码。 涉及以下任务：  
  
-   修改标头文件  
  
-   修改`OnDraw`函数  
  
-   添加计算多边形点的方法  
  
-   初始化的填充颜色  
  
## <a name="modifying-the-header-file"></a>修改标头文件  
 首先，通过添加对数学函数的支持`sin`和`cos`，将使用它计算的多边形点，并通过创建用于存储的数组置于。  
  
#### <a name="to-modify-the-header-file"></a>若要修改的标头文件  
  
1.  将行添加`#include <math.h>`PolyCtl.h 页首。 文件的顶部应如下所示：  
  
     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]  
  
2.  一旦计算的多边形点，它们将存储在类型的数组`POINT`，因此将该阵列添加后的定义`m_nSides`PolyCtl.h 中：  
  
     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]  
  
## <a name="modifying-the-ondraw-method"></a>修改 OnDraw 方法  
 现在应修改`OnDraw`PolyCtl.h 中的方法。 你将添加代码创建一个新的钢笔和画笔绘制你多边形，使用，然后调用`Ellipse`和`Polygon`Win32 API 函数来执行实际的绘图。  
  
#### <a name="to-modify-the-ondraw-function"></a>修改 OnDraw 函数  
  
1.  将现有`OnDraw`PolyCtl.h 中替换为以下代码的方法：  
  
     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]  
  
## <a name="adding-a-method-to-calculate-the-polygon-points"></a>添加计算多边形点的方法  
 添加一个方法，调用`CalcPoints`，，将计算构成此多边形的外围网络的点的坐标。 这些计算将根据传入函数 RECT 变量。  
  
#### <a name="to-add-the-calcpoints-method"></a>若要添加 CalcPoints 方法  
  
1.  添加的声明`CalcPoints`到`IPolyCtl`的公共部分`CPolyCtl`PolyCtl.h 中的类：  
  
     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]  
  
     公共部分的最后一部分`CPolyCtl`类将如下所示：  
  
     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]  
  
2.  添加的此实现的`CalcPoints`到 PolyCtl.cpp 末尾的函数：  
  
     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]  
  
## <a name="initializing-the-fill-color"></a>初始化的填充颜色  
 初始化`m_clrFillColor`默认颜色。  
  
#### <a name="to-initialize-the-fill-color"></a>若要初始化的填充颜色  
  
1.  此将行添加到将绿色用作默认颜色`CPolyCtl`PolyCtl.h 中的构造函数：  
  
     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]  
  
 构造函数现在如下所示：  
  
 [!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]  
  
## <a name="building-and-testing-the-control"></a>生成和测试控件  
 重新生成该控件。 请确保如果它仍然处于打开状态，则在关闭 PolyCtl.htm 文件，然后单击**生成多边形**上**生成**菜单。 你无法查看再次从 PolyCtl.htm 页中，控件，但这次使用 ActiveX 控件测试容器。  
  
#### <a name="to-use-the-activex-control-test-container"></a>若要使用 ActiveX 控件测试容器  
  
1.  生成并启动 ActiveX 控件测试容器。 有关详细信息，请参阅[TSTCON 示例： ActiveX 控件测试容器](../visual-cpp-samples.md)。  
  
2.  在测试容器中，在**编辑**菜单上，单击**插入新控件**。  
  
3.  查找你的控件，将调用`PolyCtl Class`，然后单击**确定**。 你将看到一个绿色三角形是圆圈。  
  
 请尝试按照下一个过程更改的边数。 若要修改上双重接口从测试容器中的属性，使用**调用方法**。  
  
#### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>若要修改从测试容器中的控件的属性  
  
1.  在测试容器中，单击**调用方法**上**控件**菜单。  
  
     **调用方法**对话框随即显示。  
  
2.  选择**PropPut**版本**边**属性从**方法名称**下拉列表框。  
  
3.  类型`5`中**参数值**框中，单击**设置值**，然后单击**Invoke**。  
  
 请注意，该控件不会更改。 虽然你的边数由内部更改设置`m_nSides`变量，这不会导致控件重绘窗体。 如果你切换到另一个应用程序并切换回测试容器，将发现该控件具有重新绘制，并具有正确的边数。  
  
 若要更正此问题，请添加对的调用`FireViewChange`在中定义的函数`IViewObjectExImpl`之后设置的边数。 如果该控件运行时在其自己的窗口中，`FireViewChange`将调用`InvalidateRect`直接的方法。 如果该控件运行时无窗口，`InvalidateRect`将在容器的站点接口上调用方法。 这将强制控件重新绘制自身。  
  
#### <a name="to-add-a-call-to-fireviewchange"></a>若要添加对 FireViewChange 的调用  
  
1.  通过添加对的调用来更新 PolyCtl.cpp`FireViewChange`到`put_Sides`方法。 完成后，`put_Sides`方法应如下所示：  
  
     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]  
  
 在添加后`FireViewChange`，重新生成，然后重试中 ActiveX 控件测试容器的控件。 此时，当您更改的边数并单击`Invoke`，你应看到立即更改该控件。  
  
 在下一步的步骤中，你将添加一个事件。  
  
 [返回到步骤 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [到步骤 5](../atl/adding-an-event-atl-tutorial-part-5.md)  
  
## <a name="see-also"></a>请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)   
 [使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)

