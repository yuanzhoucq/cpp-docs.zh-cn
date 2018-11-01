---
title: 更改绘图代码（ATL 教程，第 4 部分）
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: ce6492eb2e4da04b261c7a88154674d036bb578a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481414"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>更改绘图代码（ATL 教程，第 4 部分）

默认情况下，控件的绘制代码将显示一个正方形和文本**PolyCtl**。 在此步骤中，您将更改代码以显示一些更有趣的事情。 涉及以下任务：

- 修改标头文件

- 修改`OnDraw`函数

- 添加方法来计算多边形点

- 正在初始化的填充颜色

## <a name="modifying-the-header-file"></a>修改标头文件

首先，通过添加对数学函数的支持`sin`和`cos`，其将使用计算多边形点，并通过创建用于存储的数组来定位。

### <a name="to-modify-the-header-file"></a>若要修改标头文件

1. 将行添加`#include <math.h>`到 PolyCtl.h 的顶部。 文件的顶部应如下所示：

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. 实现`IProvideClassInfo`接口，以通过将以下代码添加到 PolyCtl.h 中提供的控件的方法信息。 在`CPolyCtl`类中，行替换为：

    ```cpp
    public CComControl<CPolyCtl>
    ```

    替换为

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    然后在`BEGIN_COM_MAP(CPolyCtl)`，可以添加几行：

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. 一旦计算多边形点，它们将存储在类型的数组`POINT`，因此定义语句后添加数组`short m_nSides;`PolyCtl.h 中：

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>修改 OnDraw 方法

现在，您应修改`OnDraw`PolyCtl.h 中的方法。 您将添加的代码创建新的笔和画笔用于绘制在多边形，然后调用`Ellipse`和`Polygon`Win32 API 函数来执行实际绘制。

### <a name="to-modify-the-ondraw-function"></a>修改 OnDraw 函数

1. 替换现有`OnDraw`PolyCtl.h 中使用以下代码的方法：

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>添加方法来计算多边形点

添加一个方法，名为`CalcPoints`，将计算构成了多边形的外围网络的点的坐标。 这些计算将基于传递到函数的 RECT 变量。

### <a name="to-add-the-calcpoints-method"></a>若要添加 CalcPoints 方法

1. 添加的声明`CalcPoints`到`IPolyCtl`的公共部分`CPolyCtl`PolyCtl.h 中的类：

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    公共部分的最后一个部分`CPolyCtl`类将如下所示：

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. 添加的这一实现`CalcPoints`PolyCtl.cpp 结束函数：

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>正在初始化的填充颜色

初始化`m_clrFillColor`默认颜色。

### <a name="to-initialize-the-fill-color"></a>若要初始化的填充颜色

1. 使用默认颜色为绿色，添加此代码行`CPolyCtl`PolyCtl.h 中的构造函数：

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

构造函数现在如下所示：

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>生成和测试控件

重新生成该控件。 请确保它是否仍然打开，请关闭 PolyCtl.htm 文件，然后单击**生成多边形**上**生成**菜单。 您可以查看该控件再一次从 PolyCtl.htm 页上，但这次使用 ActiveX 控件测试容器。

### <a name="to-use-the-activex-control-test-container"></a>若要使用 ActiveX 控件测试容器

1. 生成并启动 ActiveX 控件测试容器。 [TSTCON 示例： ActiveX 控件测试容器](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon)可在 GitHub 上找到。

    > [!NOTE]
    > 错误涉及`ATL::CW2AEX`，在 Script.Cpp，将为行`TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );`与`TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`，和行`TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );`与`TRACE( "Source Text: %s\n", bstrSourceLineText );`。<br/>
    > 错误涉及`HMONITOR`，打开在 StdAfx.h`TCProps`项目，并替换为：
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    > 替换为
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. 在中**测试容器**，然后在**编辑**菜单中，单击**插入新控件**。

1. 查找您的控件，将调用`PolyCtl class`，然后单击**确定**。 你将看到一个绿色三角形是圆圈。

请尝试更改边数的下一步的过程。 若要修改上双重接口中的属性**测试容器**，使用**调用方法**。

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>若要修改从测试容器中的控件的属性

1. 在中**测试容器**，单击**调用方法**上**控制**菜单。

    **调用方法**显示对话框。

1. 选择**PropPut**新版**边**属性从**方法名称**下拉列表框。

1. 类型`5`中**参数值**框中，单击**设置值**，然后单击**Invoke**。

请注意，该控件不会更改。 尽管您进行了更改的边数在内部设置`m_nSides`变量，这是否会导致控件重绘。 如果切换到另一个应用程序的虚拟机和模板，然后切换回**测试容器**，您会发现该控件具有重新绘制，并具有正确的边数。

若要更正此问题，请添加对的调用`FireViewChange`中定义的函数`IViewObjectExImpl`之后设置的边数。 如果该控件在其自己的窗口中，运行时`FireViewChange`将调用`InvalidateRect`直接方法。 如果该控件运行时无窗口，`InvalidateRect`将容器的站点接口上调用方法。 这会强制控件重绘其自身。

### <a name="to-add-a-call-to-fireviewchange"></a>若要添加对 FireViewChange 的调用

1. 通过添加对的调用更新 PolyCtl.cpp`FireViewChange`到`put_Sides`方法。 完成后，`put_Sides`方法应如下所示：

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

添加后`FireViewChange`、 重新生成，然后重试中 ActiveX 控件测试容器的控件。 这一次时更改边数，单击`Invoke`，应会看到控件立即更改。

在下一步中，将添加一个事件。

[返回到步骤 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [到步骤 5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>请参阅

[教程](../atl/active-template-library-atl-tutorial.md)<br/>
[使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)
