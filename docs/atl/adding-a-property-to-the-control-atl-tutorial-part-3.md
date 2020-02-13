---
title: 向控件中添加属性（ATL 教程，第 3 部分）
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 288dc9f5af57c02639d15a9a971419a633cfc08d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127582"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>向控件中添加属性（ATL 教程，第 3 部分）

`IPolyCtl` 是包含控件的自定义方法和属性的接口，您将向其添加属性。

### <a name="to-add-the-property-definitions-to-your-project"></a>将属性定义添加到项目中

1. 在**类视图**中，展开 "`Polygon`" 分支。

1. 右键单击 `IPolyCtl`。

1. 在快捷菜单上，单击 "**添加**"，然后单击 "**添加属性**"。 "**添加属性**向导" 随即出现。

1. 将 `Sides` 键入为**属性名称**。

1. 在 "**属性类型**" 下拉列表中，选择 "`short`"。

1. 单击 **"确定"** 完成添加属性。

1. 在**解决方案资源管理器**中，打开多边形 .idl 并在 `IPolyCtl : IDispatch` 接口的末尾替换以下行：

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    替换为

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. 在**解决方案资源管理器**中，打开 polyctl.htm，并在 `m_clrFillColor`的定义后添加以下行：

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

尽管你现在具有用于设置和检索属性的框架函数和用于存储属性的变量，但你必须相应地实现函数。

### <a name="to-update-the-get-and-put-methods"></a>更新 get 和 put 方法

1. 设置 `m_nSides`的默认值。 将行添加到 Polyctl.htm 中的构造函数，使默认形状成为三角形：

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. 实现 `Get` 和 `Put` 方法。 已将 `get_Sides` 和 `put_Sides` 函数声明添加到 Polyctl.htm。 现在，将 `get_Sides` 和 `put_Sides` 的代码添加到 Polyctl.htm，如下所示：

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

`get_Sides` 方法通过 `pVal` 指针返回 `Sides` 属性的当前值。 在 `put_Sides` 方法中，代码确保用户将 `Sides` 属性设置为可接受的值。 最小值必须为3，因为每一侧都将使用点数组，100是最大值的合理限制。

现在，你有一个名为 `Sides`的属性。 在下一步中，你将更改绘图代码以使用该代码。

返回到[步骤4中的](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)[步骤 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124;

## <a name="see-also"></a>另请参阅

[教程](../atl/active-template-library-atl-tutorial.md)
