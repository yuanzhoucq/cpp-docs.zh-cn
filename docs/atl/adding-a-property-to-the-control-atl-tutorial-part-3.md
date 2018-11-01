---
title: 向控件中添加属性（ATL 教程，第 3 部分）
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 9b8744e964274acb35c32a1ace02f71d0fed5c2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466854"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>向控件中添加属性（ATL 教程，第 3 部分）

`IPolyCtl` 是接口，它包含控件的自定义方法和属性，并将向其添加属性。

### <a name="to-add-the-property-definitions-to-your-project"></a>若要添加到你的项目的属性定义

1. 在中**类视图**，展开`Polygon`分支。

1. 右键单击`IPolyCtl`。

1. 在快捷菜单上，单击**外**，然后单击**添加属性**。 **添加属性**向导将显示。

1. 类型`Sides`作为**属性名称**。

1. 在下拉列表中**属性类型**，选择`short`。

1. 单击**确定**以完成添加属性。

1. 从**解决方案资源管理器**，打开 polygon.idl 使其并将以下行的末尾`IPolyCtl : IDispatch`接口：

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    替换为

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. 从**解决方案资源管理器**，打开 PolyCtl.h 并添加以下行后的定义`m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

尽管您现在可以使用主干函数设置和检索的属性和一个变量来存储属性，则必须相应地实现函数。

### <a name="to-update-the-get-and-put-methods"></a>若要更新 get 和 put 方法

1. 设置的默认值`m_nSides`。 请通过将行添加到 PolyCtl.h 中的构造函数中形状的三角形的默认值：

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. 实现`Get`和`Put`方法。 `get_Sides`和`put_Sides`已添加到 PolyCtl.h 函数声明。 现在，添加的代码`get_Sides`和`put_Sides`到 PolyCtl.cpp 以下：

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

`get_Sides`方法返回的当前值`Sides`通过属性`pVal`指针。 在中`put_Sides`方法，该代码可确保用户设置`Sides`属性设置为可接受的值。 最小值必须是 3，并且点数组将用于每一方，因为 100 是合理的最大值限制。

现在有一个名为属性`Sides`。 在下一步，您将更改绘图代码即可使用它。

[返回到步骤 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [到步骤 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>请参阅

[教程](../atl/active-template-library-atl-tutorial.md)
