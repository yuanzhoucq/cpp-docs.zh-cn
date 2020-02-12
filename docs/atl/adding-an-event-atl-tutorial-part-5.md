---
title: 添加事件（ATL 教程，第 5 部分）
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: c9a7c6f38a2f47ec808081e440a200737ad1928a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127569"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>添加事件（ATL 教程，第 5 部分）

在此步骤中，你将向 ATL 控件添加 `ClickIn` 和 `ClickOut` 事件。 如果用户在多边形内单击并在用户单击外部时激发 `ClickOut`，则会激发 `ClickIn` 事件。 用于添加事件的任务如下所示：

- 添加 `ClickIn` 和 `ClickOut` 方法

- 生成类型库

- 实现连接点接口

## <a name="adding-the-clickin-and-clickout-methods"></a>添加 ClickIn 和 ClickOut 方法

当你在步骤2中创建 ATL 控件时，你选择了 "**连接点**" 复选框。 这会在多边形 .idl 文件中创建 `_IPolyCtlEvents` 接口。 请注意，接口名称以下划线开头。 这是一种约定，指示该接口是一个内部接口。 因此，允许您浏览 COM 对象的程序可以选择不显示用户界面。 另请注意，选择 "**连接点**" 会在多边形 .idl 文件中添加以下行，以指示 `_IPolyCtlEvents` 为默认源接口：

`[default, source] dispinterface _IPolyCtlEvents;`

Source 特性指示控件是通知的源，因此它将在容器上调用此接口。

现在，将 `ClickIn` 和 `ClickOut` 方法添加到 `_IPolyCtlEvents` 接口。

### <a name="to-add-the-clickin-and-clickout-methods"></a>添加 ClickIn 和 ClickOut 方法

1. 在**解决方案资源管理器**中，打开多边形 .idl 并将以下代码添加到 PolygonLib 库的 `dispInterface_IPolyCtlEvents` 声明中的 `methods:`：

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

`ClickIn` 和 `ClickOut` 方法采用所单击的点的 x 和 y 坐标作为参数。

## <a name="generating-the-type-library"></a>生成类型库

此时生成类型库，因为项目将使用它来获取构造连接点接口所需的信息，以及用于控件的连接点容器接口。

### <a name="to-generate-the-type-library"></a>生成类型库

1. 重新生成项目。

     \- 或 -

1. 在**解决方案资源管理器**中右键单击多边形 .idl 文件，然后单击快捷菜单上的 "**编译**"。

这将创建多边形 .tlb 文件，即类型库。 **解决方案资源管理器**中不显示多边形 .tlb 文件，因为该文件是二进制文件，无法直接查看或编辑。

## <a name="implementing-the-connection-point-interfaces"></a>实现连接点接口

为控件实现连接点接口和连接点容器接口。 在 COM 中，事件是通过连接点机制实现的。 为了从 COM 对象接收事件，容器与 COM 对象实现的连接点建立了通知连接。 由于 COM 对象可以有多个连接点，因此 COM 对象还实现连接点容器接口。 通过此接口，容器可以确定支持哪些连接点。

实现连接点的接口称为 `IConnectionPoint`，实现连接点容器的接口 `IConnectionPointContainer`调用。

为了帮助实现 `IConnectionPoint`，你将使用 "实现连接点向导"。 此向导通过读取类型库并为可以激发的每个事件实现函数来生成 `IConnectionPoint` 接口。

### <a name="to-implement-the-connection-points"></a>实现连接点

1. 在**解决方案资源管理器**中，打开 _IPolyCtlEvents_CP，然后在 `CProxy_IPolyCtlEvents` 类中的 `public:` 语句下添加以下代码：

    ```cpp
    VOID Fire_ClickIn(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x1, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    VOID Fire_ClickOut(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x2, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    ```

您将看到此文件具有从 `IConnectionPointImpl`派生的名为 `CProxy_IPolyCtlEvents` 的类。 _IPolyCtlEvents_CP 现在定义了两个方法 `Fire_ClickIn` 和 `Fire_ClickOut`，它们采用两个坐标参数。 如果要从控件激发事件，请调用这些方法。

通过创建 "具有**连接点**的控件" 选项，将为您生成 _IPolyCtlEvents_CP .h 文件。 它还将 `CProxy_PolyEvents` 和 `IConnectionPointContainerImpl` 添加到控件的多个继承列表，并通过将相应的项添加到 COM 映射来向你公开 `IConnectionPointContainer`。

你完成了实现代码以支持事件的操作。 现在，添加一些代码，以便在适当的时间触发事件。 请记住，当用户在控件中单击鼠标左键时，将激发 `ClickIn` 或 `ClickOut` 事件。 若要确定用户何时单击按钮，请为 `WM_LBUTTONDOWN` 消息添加处理程序。

### <a name="to-add-a-handler-for-the-wm_lbuttondown-message"></a>为 WM_LBUTTONDOWN 消息添加处理程序

1. 在**类视图**中，右键单击 `CPolyCtl` 类，然后单击快捷菜单上的 "**属性**"。

1. 在 "**属性**" 窗口中，单击 "**消息**" 图标，然后单击左侧列表中的 "`WM_LBUTTONDOWN`"。

1. 从显示的下拉列表中，单击 " **\<添加 > OnLButtonDown**"。 `OnLButtonDown` 处理程序声明将添加到 Polyctl.htm，并且处理程序实现将添加到 Polyctl.htm 中。

接下来，修改处理程序。

### <a name="to-modify-the-onlbuttondown-method"></a>修改 OnLButtonDown 方法

1. 更改包含 Polyctl.htm 中的 `OnLButtonDown` 方法（删除向导所放置的任何代码）的代码，使其看起来像这样：

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

此代码使用 `OnDraw` 函数中计算的点创建一个区域，该区域通过调用 `PtInRegion`来检测用户的鼠标单击。

*UMsg*参数是所处理的 Windows 消息的 ID。 这使您可以使用一个函数来处理消息范围。 *WParam*和*lParam*参数是要处理的消息的标准值。 参数*bHandled*允许指定函数是否处理消息。 默认情况下，该值设置为 TRUE 以指示该函数处理了该消息，但您可以将其设置为 FALSE。 这将导致 ATL 继续查找要将消息发送到的另一消息处理程序函数。

## <a name="building-and-testing-the-control"></a>生成和测试控件

现在尝试您的事件。 生成控件并再次启动 ActiveX 控件测试容器。 此时，查看 "事件日志" 窗口。 若要将事件路由到输出窗口，请单击 "**选项**" 菜单中的 "**日志记录**"，然后选择 "**记录到输出窗口**"。 插入控件并尝试在窗口中单击。 请注意，如果在填充多边形内单击并在其外单击时触发 `ClickOut`，则会触发 `ClickIn`。

接下来，您将添加一个属性页。

[返回](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [到步骤4，直到步骤 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>另请参阅

[教程](../atl/active-template-library-atl-tutorial.md)
