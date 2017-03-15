---
title: "添加事件（ATL 教程，第 5 部分） | Microsoft Docs"
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
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 添加事件（ATL 教程，第 5 部分）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在此步骤中，您将添加 `ClickIn` 和一个 `ClickOut` 事件向ATL控件。  将激发 `ClickIn` 事件，如果用户在多边形和。`ClickOut` 中单击，如果用户单击外部。  任务添加事件如下所示:  
  
-   添加 `ClickIn` 和 `ClickOut` 方法  
  
-   生成类型库  
  
-   实现连接点接口  
  
## 添加ClickIn和ClickOut方法  
 当您在步骤2中创建的ATL控件，您选择了 **连接点** 复选框。  这在Polygon.idl文件创建了 `_IPolyCtlEvents` 接口。  请注意接口名称以下划线开头。  这是指示约定接口是一个内部接口。  因此，允许您浏览COM对象的程序可能不会选择公开接口给用户。  另外请注意选择 **连接点** 的实例添加到Polygon.idl文件中的以下行指示 `_IPolyCtlEvents` 是默认源接口:  
  
 `[default, source] dispinterface _IPolyCtlEvents;`  
  
 源属性指示该控件是通知的源，因此，它将调用容器的此接口。  
  
 现在添加 `ClickIn` 和 `ClickOut` 方法。`_IPolyCtlEvents` 接口。  
  
#### 添加ClickIn和ClickOut方法  
  
1.  在选件类视图"中，展开多边形和PolygonLib显示\_IPolyCtlEvents。  
  
2.  右击\_IPolyCtlEvents。  在快捷菜单上单击“添加”，然后单击“添加方法”。  
  
3.  选择 `void`**返回类型**。  
  
4.  在 **方法名称** 框中输入 `ClickIn`。  
  
5.  在 **参数属性**下，选择 **在** 框。  
  
6.  选择 `LONG`**参数类型**。  
  
7.  键入 `x` 作为 **参数名**，然后单击 **添加**。  
  
8.  重复步骤5到步骤7，这次针对 **参数名** of `y` 的查询。  
  
9. 单击**“下一步”**。  
  
10. 键入 `方法ClickIn` 作为 **helpstring**。  
  
11. 单击**“完成”**。  
  
12. 重复上述步骤定义具有相同 `LONG` 参数 `x` 的一个 `ClickOut` 方法，并 `y`、同样 **参数属性** 和相同 `void` 返回类型。  
  
 检查Polygon.idl文件以了解代码添加到 `_IPolyCtlEvents` 调度接口。  
  
 在您的Polygon.idl文件的 `_IPolyCtlEvents` 调度接口现在应如下所示:  
  
 [!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/CPP/adding-an-event-atl-tutorial-part-5_1.idl)]  
  
 `ClickIn` 和 `ClickOut` 方法采用x，然后单击的Y坐标磅作为参数。  
  
## 生成类型库  
 此时生成类型库，因为连接点向导将使用需要构造连接点接口的以获取信息，并连接点控件的容器接口。  
  
#### 生成类型库  
  
1.  重新生成项目。  
  
     \- 或 \-  
  
2.  右击在解决方案资源管理器中Polygon.idl文件并单击 **生成** 在快捷菜单上。  
  
 这将创建Polygon.tlb文件，即您的类型库。  因为它是二进制文件，不能直接，可以查看或编辑Polygon.tlb文件从解决方案资源管理器中不可见。  
  
## 实现连接点接口  
 实现连接点接口，并且连接点控件的容器接口。  在COM，事件将结构实现连接点。  若要接收来自COM对象的事件，容器建立与的建议使用性连接连接点COM对象实现。  由于COM对象可以有多个连接点，COM对象还实现连接点容器接口。  通过此接口，容器可以确定连接点支持。  
  
 实现连接点的接口调用，`IConnectionPoint`，并实现的接口的连接点容器调用 `IConnectionPointContainer`。  
  
 为了帮助实现 `IConnectionPoint`，您将使用"实现连接点向导。  此向导通过读取您的类型库和实现中激发的每个事件的函数生成 `IConnectionPoint` 接口。  
  
#### 若要使用"实现连接点向导  
  
1.  在选件类视图中，右击您的控件的实现选件类 `CPolyCtl`。  
  
2.  在快捷菜单上，单击 **添加**，然后单击 **添加连接点**。  
  
3.  从 **源接口** 的SELECT `_IPolyCtlEvents` 列表并双击它添加到 **实现连接点** 列。  单击**“完成”**。  的代理选件类联接会生成，在这种情况下，`CProxy_IPolyCtlEvents`。  
  
 如果您在解决方案资源管理器中生成的\_IPolyCtlEvents\_CP.h文件，您会看到它具有从派生 `IConnectionPointImpl`调用 `CProxy_IPolyCtlEvents` 的选件类。  \_IPolyCtlEvents\_CP.h还定义了两个方法 `Fire_ClickIn` 和 `Fire_ClickOut`，采用两个协调参数。  当您将激发从控件时，的事件您调用这些方法。  
  
 该向导还添加了 `CProxy_PolyEvents`，并对控件的多重继承的 `IConnectionPointContainerImpl` 列表。  向导通过添加相应的项还显示了 `IConnectionPointContainer` 到COM映射。  
  
 您完成实现代码支持事件。  现在，添加一些代码适逢其时激发事件。  当用户单击控件时，的鼠标左键请记住，将激发 `ClickIn` 或 `ClickOut` 事件。  若要查找有关中所列用户何时单击按钮，添加 `WM_LBUTTONDOWN` 消息处理程序。  
  
#### 添加WM\_LBUTTONDOWN消息处理程序  
  
1.  在选件类视图中，右击CPolyCtl选件类并单击 **属性** 在快捷菜单上。  
  
2.  在 **属性** 窗口中，单击 **消息** 图标然后单击从列表中 `WM_LBUTTONDOWN` 左侧。  
  
3.  从显示的下拉列表中，单击 **\<Add\>  OnLButtonDown**。  `OnLButtonDown` 处理程序声明将添加到PolyCtl.h，因此，处理程序实现将添加到PolyCtl.cpp。  
  
 接下来，修改处理程序。  
  
#### 修改OnLButtonDown方法  
  
1.  更改包括在PolyCtl.cpp的 `OnLButtonDown` 方法的代码\(删除向导中的任何代码\)，以便如下所示:  
  
     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/CPP/adding-an-event-atl-tutorial-part-5_2.cpp)]  
  
 此代码在 `OnDraw` 功能利用点计算创建检测与调用的用户的鼠标单击以 `PtInRegion`的区域。  
  
 `uMsg` 参数被处理的Windows消息的ID。  这允许您有一个函数处理消息的大小。  `wParam` 和 `lParam` 参数被处理消息的标准值。  bHandled的参数用于指定是否函数处理该消息。  默认情况下，该值设置为 `TRUE` 指示功能处理该消息，但是，您可以将其设置为 `FALSE`。  这将使ATL继续查找另一个消息处理函数发送消息。  
  
## 生成并测试控件  
 现在即可测试您的操作。  生成控件并重新启动ActiveX控件测试容器。  此时，查看事件日志窗口。  将事件"输出"窗口，请单击该 **选项** 菜单的 **记录** 并选择 **登录到输出窗口**。  插入单击的控件和的尝试在窗口中。  请注意 `ClickIn` 会激发，如果在已填充的多边形中，单击，然后 `ClickOut` 会激发，在\+外单击它。  
  
 接下来，您将添加属性页。  
  
 [返回第4步](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [在到步骤6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## 请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)