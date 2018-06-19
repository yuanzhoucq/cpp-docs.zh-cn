---
title: 添加事件 (ATL 教程，第 5) |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a118cf29546ac8dae2e882d5658b07e3b5e085f6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361260"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>添加事件（ATL 教程，第 5 部分）
在此步骤中，你将添加`ClickIn`和`ClickOut`ATL 控件的事件。 将激发`ClickIn`事件，如果用户单击中的多边形和火灾`ClickOut`如果用户单击之外。 要添加一个事件的任务如下所示：  
  
-   添加`ClickIn`和`ClickOut`方法  
  
-   生成类型库  
  
-   实现连接点接口  
  
## <a name="adding-the-clickin-and-clickout-methods"></a>添加 ClickIn 和 ClickOut 方法  
 当你在步骤 2 中创建 ATL 控件时，你选择**连接点**复选框。 这创建`_IPolyCtlEvents`Polygon.idl 文件中的接口。 请注意，接口名称以下划线开头。 这是以指示该接口是内部接口的约定。 因此，允许你浏览 COM 对象的程序可以选择不希望向用户显示接口。 此外请注意，选择**连接点**Polygon.idl 文件，则指示中添加以下行`_IPolyCtlEvents`是默认源接口：  
  
 `[default, source] dispinterface _IPolyCtlEvents;`  
  
 源属性指示控件通知的源，以便它将在容器上调用此接口。  
  
 现在添加`ClickIn`和`ClickOut`方法`_IPolyCtlEvents`接口。  
  
#### <a name="to-add-the-clickin-and-clickout-methods"></a>若要添加的 ClickIn 和 ClickOut 方法  
  
1.  在类视图中，展开多边形和 PolygonLib 以显示 _IPolyCtlEvents。  
  
2.  右键单击 _IPolyCtlEvents。 在快捷菜单上，单击**添加**，然后单击**添加方法**。  
  
3.  选择**返回类型**的`void`。  
  
4.  输入`ClickIn`中**方法名称**框。  
  
5.  下**参数属性**，选择**中**框。  
  
6.  选择**参数类型**的`LONG`。  
  
7.  类型`x`作为**参数名称**，然后单击**添加**。  
  
8.  重复步骤 5 到 7，这一次**参数名称**的`y`。  
  
9. 单击 **“下一步”**。  
  
10. 类型`method ClickIn`作为**helpstring**。  
  
11. 单击 **“完成”**。  
  
12. 重复上述步骤以定义`ClickOut`具有相同的方法`LONG`参数`x`和`y`，相同**参数属性**和同一`void`返回类型。  
  
 检查 Polygon.idl 文件以查看代码已添加到`_IPolyCtlEvents`调度接口。  
  
 `_IPolyCtlEvents` Polygon.idl 文件中的调度接口现在应如下所示：  
  
 [!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_1.idl)]  
  
 `ClickIn`和`ClickOut`方法 take x 和 y 坐标的单击的点作为参数。  
  
## <a name="generating-the-type-library"></a>生成类型库  
 在这种情况下，生成类型库，因为连接点向导将使用它来获取它需要构造的连接点接口和连接点容器接口为您的控件的信息。  
  
#### <a name="to-generate-the-type-library"></a>若要生成类型库  
  
1.  重新生成项目。  
  
     -或-  
  
2.  右键单击解决方案资源管理器中的 Polygon.idl 文件，然后单击**编译**快捷菜单上。  
  
 这将创建 Polygon.tlb 文件，它是类型库。 因为它是二进制文件，无法查看或直接编辑，Polygon.tlb 文件不是从解决方案资源管理器中看到显示的值。  
  
## <a name="implementing-the-connection-point-interfaces"></a>实现连接点接口  
 实现连接点接口和控件的连接点容器接口。 在 COM 中，事件将通过连接点的机制来实现。 若要从 COM 对象接收事件，容器建立的连接点，该 COM 对象实现的通知连接。 COM 对象可以具有多个连接点，因为 COM 对象还实现连接点容器接口。 通过此接口，容器可以确定支持哪些连接点。  
  
 实现连接点的接口称为`IConnectionPoint`，和实现连接点容器的接口称为`IConnectionPointContainer`。  
  
 来帮助实施`IConnectionPoint`，你将使用实现连接点向导。 此向导将生成`IConnectionPoint`通过读取类型库并为每个事件可以触发函数的实现的接口。  
  
#### <a name="to-use-the-implement-connection-point-wizard"></a>用于实现连接点向导  
  
1.  在类视图中，右键单击控件的实现类`CPolyCtl`。  
  
2.  在快捷菜单上，单击**添加**，然后单击**添加连接点**。  
  
3.  选择`_IPolyCtlEvents`从**源接口**列表并双击它以将其添加到**实现连接点**列。 单击 **“完成”**。 连接点的代理类将生成，在这种情况下， `CProxy_IPolyCtlEvents`。  
  
 如果你看一下在解决方案资源管理器中的生成的 _IPolyCtlEvents_CP.h 文件，你将看到它具有一个名为类`CProxy_IPolyCtlEvents`派生自`IConnectionPointImpl`。 _IPolyCtlEvents_CP.h 还定义了两个方法`Fire_ClickIn`和`Fire_ClickOut`，这需要两个坐标参数。 当你想要激发来自控件的事件时调用这些方法。  
  
 向导还添加`CProxy_PolyEvents`和`IConnectionPointContainerImpl`到控件的多个继承列表。 向导还公开`IConnectionPointContainer`为你通过将相应的条目添加到 COM 映射。  
  
 您已完成实现以支持事件的代码。 现在，添加一些代码以在适当的时候激发事件。 请记住，你要激发`ClickIn`或`ClickOut`当用户单击鼠标左键在控件中的事件。 若要找出用户单击按钮时，将添加的处理程序`WM_LBUTTONDOWN`消息。  
  
#### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>若要添加的处理程序 WM_LBUTTONDOWN 消息  
  
1.  在类视图中，右键单击 CPolyCtl 类，然后单击**属性**快捷菜单上。  
  
2.  在**属性**窗口中，单击**消息**图标，然后单击`WM_LBUTTONDOWN`从左侧列表。  
  
3.  从下拉列表中显示，请单击**\<添加 > OnLButtonDown**。 `OnLButtonDown`处理程序声明将添加到 PolyCtl.h，并处理程序实现将添加到 PolyCtl.cpp。  
  
 接下来，修改该处理程序。  
  
#### <a name="to-modify-the-onlbuttondown-method"></a>若要修改 OnLButtonDown 方法  
  
1.  更改代码包括`OnLButtonDown`PolyCtl.cpp （删除由向导放置的任何代码） 中的方法，以便其类似如下所示：  
  
     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]  
  
 使用点中计算此代码使`OnDraw`函数来创建检测到用户的鼠标单击调用一个区域`PtInRegion`。  
  
 `uMsg`参数是正在处理的 Windows 消息的 ID。 这样，您可以处理一系列消息的一个函数。 `wParam`和`lParam`参数是正在处理的消息的标准值。 参数 bHandled，可指定或不函数是否处理消息。 默认情况下，值设置为`TRUE`表明函数处理消息，但你可以将其设置为`FALSE`。 这将导致 ATL 继续寻找另一个要发送到消息的消息处理程序函数。  
  
## <a name="building-and-testing-the-control"></a>生成和测试控件  
 现在尝试您的事件。 生成控件，再次启动 ActiveX 控件测试容器。 这一次，查看事件日志窗口。 若要将事件路由到输出窗口，请单击**日志记录**从**选项**菜单，然后选择**日志到输出窗口**。 插入控件并尝试在窗口中单击。 请注意，`ClickIn`如果您在已填充的多边形，单击激发和`ClickOut`在外部单击时被激发。  
  
 接下来，你将添加属性页。  
  
 [返回到步骤 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [到步骤 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="see-also"></a>请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)

