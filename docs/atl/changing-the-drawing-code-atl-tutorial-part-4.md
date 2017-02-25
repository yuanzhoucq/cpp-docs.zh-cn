---
title: "更改绘图代码（ATL 教程，第 4 部分） | Microsoft Docs"
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
helpviewer_keywords: 
  - "_ATL_MIN_CRT 宏"
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 更改绘图代码（ATL 教程，第 4 部分）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，控件的绘图代码演示正方形和该文本 **PolyCtl**。  在此步骤中，您将更改代码演示更加有趣的操作。  以下任务是包含的:  
  
-   修改标头文件  
  
-   修改 `OnDraw` 功能  
  
-   添加方法计算多边形点  
  
-   初始化填充颜色  
  
## 修改标头文件  
 首先添加用于数学函数 `sin` 和 `cos`支持，将使用计算多边形通过创建数组存储位置点，和。  
  
#### 修改标头文件  
  
1.  添加行 `#include <math.h>` 到PolyCtl.h顶部。  文件的顶部应如下所示:  
  
     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]  
  
2.  对于多边形点计算，它们在数组中存储类型 `POINT`，因此，请在 `m_nSides` 的定义稍后在PolyCtl.h的添加数组:  
  
     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_2.h)]  
  
## 修改OnDraw方法  
 现在您应修改在PolyCtl.h的 `OnDraw` 方法。  将添加的代码创建绘制您的多边形，然后调用 `Ellipse` 和 `Polygon` Win32 API函数来执行实际的绘制的一个新的钢笔和画笔。  
  
#### 修改OnDraw功能  
  
1.  用下面的代码替换该PolyCtl.h的现有 `OnDraw` 方法:  
  
     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]  
  
## 添加方法计算多边形点  
 添加一个方法，调用 `CalcPoints`，将计算坐标点组成周长多边形。  这些计算基于传递给函数的RECT变量。  
  
#### 添加CalcPoints方法  
  
1.  添加 `CalcPoints` 的声明添加到 `CPolyCtl` 选件类的 `IPolyCtl` public节中PolyCtl.h的:  
  
     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_4.h)]  
  
     `CPolyCtl` 选件类的public节中的最后一部分如下所示:  
  
     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_5.h)]  
  
2.  添加 `CalcPoints` 功能的此实现。PolyCtl.cpp的末尾:  
  
     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]  
  
## 初始化填充颜色  
 初始化默认颜色的 `m_clrFillColor`。  
  
#### 初始化填充颜色  
  
1.  使用绿色，默认颜色通过将此行添加到PolyCtl.h的 `CPolyCtl` 构造函数:  
  
     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_7.h)]  
  
 构造函数现在如下所示:  
  
 [!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_8.h)]  
  
## 生成并测试控件  
 重新生成该控件。  确定PolyCtl.htm文件已关闭，如果该节点是打开的，然后单击 **生成多边形** 在 **生成** 菜单。  可以再次查看控件从PolyCtl.htm页，但是，这次使用ActiveX控件测试容器。  
  
#### 若要使用ActiveX控件测试容器  
  
1.  生成并启动ActiveX控件测试容器。  有关更多信息，请参见 [TSTCON示例:ActiveX控件测试容器](../top/visual-cpp-samples.md)。  
  
2.  在测试容器中，在 **编辑** 菜单上，单击 **插入新的控件**。  
  
3.  定位控件，将调用 `PolyCtl Class`然后单击 **确定**。  您将看到一个绿色圆圈中三角形。  
  
 尝试更改边数按照下一过程。  若要修改在双重接口的属性从内部测试容器中，使用 **Invoke Methods**。  
  
#### 修改控件的属性从测试容器的内部  
  
1.  在测试容器中，在 **控件** 菜单中单击 **调用方法**。  
  
     **调用方法** 显示对话框。  
  
2.  选择 **Sides** 属性的 **PropPut** 版本中的 **方法名称** 下拉式列表框。  
  
3.  键入在 **参数值** 框中 `5`，单击 **设置值**，然后单击 **调用**。  
  
 请注意控件不会更改。  尽管您通过设置 `m_nSides` 变量在内部更改了边数，则不会使控件重新绘制。  如果您对另一个应用程序的开关切换回然后测试容器，您会看到控件重新绘制并具有端的正确数目。  
  
 在设置端后，数若要更正此问题，请添加对的调用 `FireViewChange` 功能，定义在 `IViewObjectExImpl`。  如果控件在其自己的windows上运行，`FireViewChange` 将直接调用 `InvalidateRect` 方法。  如果该控件是运行无窗口，`InvalidateRect` 方法是在容器的站点接口。  这会强制该控件重新绘制自身。  
  
#### 添加对FireViewChange  
  
1.  通过将调用更新PolyCtl.cpp到 `FireViewChange` 到 `put_Sides` 方法。  完成后，`put_Sides` 方法应如下所示:  
  
     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]  
  
 在添加 `FireViewChange`之后，重新生成并尝试再次控件在ActiveX控件测试容器。  这次，当您更改边数然后单击 `Invoke`时，应立即看到控件中。  
  
 在下一步，您将添加一个事件。  
  
 [返回第3步](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [在到步骤5](../atl/adding-an-event-atl-tutorial-part-5.md)  
  
## 请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)   
 [使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)