---
title: 将属性添加到控件 (ATL 教程，第 3) |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cbfb0b22579aceb5cbee196e3c5eda3079c9304
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848712"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>向控件中添加属性（ATL 教程，第 3 部分）
`IPolyCtl` 是接口，它包含控件的自定义方法和属性，并将向其添加属性。  
  
### <a name="to-add-a-property-using-the-add-property-wizard"></a>若要使用添加属性向导添加属性  
  
1.  在类视图中，展开多边形分支。  
  
2.  右键单击 IPolyCtl。  
  
3.  在快捷菜单上，单击**外**，然后单击**添加属性**。  
  
     将显示添加属性向导。  
  
4.  在属性类型下拉列表列表中，选择`SHORT`。  
  
5.  类型*边*作为**属性名称。**  
  
6.  单击**完成**以完成添加属性。  
  
 MIDL （.idl 文件编译的程序） 时向接口添加属性，定义`Get`方法，以检索其值和一个`Put`方法用于设置新值。 方法通过预先计算的命名`put_`和`get_`的属性名称。  
  
 添加属性向导将所需的行添加到.idl 文件中。 它还添加了`Get`和`Put`函数原型到 PolyCtl.h 中的类定义，并将空实现添加到 PolyCtl.cpp。 您可以通过打开 PolyCtl.cpp 并寻找函数检查这`get_Sides`和`put_Sides`。  
  
 尽管现在具有主干函数来设置和检索属性，但它需要一个位置来存储。 您将创建一个变量来存储属性并相应地更新函数。  
  
#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>若要创建一个变量以存储属性，并更新 put 和 get 方法  
  
1.  从解决方案资源管理器，打开 PolyCtl.h 和后面的定义添加以下行`m_clrFillColor`:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  设置的默认值`m_nSides`。 请通过将行添加到 PolyCtl.h 中的构造函数中形状的三角形的默认值：  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  实现`Get`和`Put`方法。 `get_Sides`和`put_Sides`已添加到 PolyCtl.h 函数声明。 替换为 PolyCtl.cpp 中的代码`get_Sides`和`put_Sides`使用以下代码：  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 `get_Sides`方法返回的当前值`Sides`通过属性`pVal`指针。 在中`put_Sides`方法，该代码可确保用户设置`Sides`属性设置为可接受的值。 最小值必须是 3，并且点数组将用于每一方，因为 100 是合理的最大值限制。  
  
 现在有一个名为属性`Sides`。 在下一步，您将更改绘图代码即可使用它。  
  
 [返回到步骤 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [到步骤 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## <a name="see-also"></a>请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)

