---
title: "将属性添加到控件 (ATL 教程，第 3 部分) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f9bd5890dbe73cfcd99b2c3b37a25618775f592e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>向控件中添加属性（ATL 教程，第 3 部分）
`IPolyCtl`是接口，包含控件的自定义方法和属性，并将向其添加属性。  
  
### <a name="to-add-a-property-using-the-add-property-wizard"></a>若要使用添加属性向导添加属性  
  
1.  在类视图中，展开多边形分支。  
  
2.  右键单击 IPolyCtl。  
  
3.  在快捷菜单上，单击**添加**，然后单击**添加属性**。  
  
     添加属性向导将显示。  
  
4.  在属性类型下拉列表列表中，选择`SHORT`。  
  
5.  类型`Sides`作为**属性名称。**  
  
6.  单击**完成**以完成添加属性。  
  
 MIDL （将.idl 文件编译的程序） 时向接口添加属性，定义`Get`用于检索其值的方法和一个`Put`方法用于设置新值。 这些方法的命名通过预先计算`put_`和`get_`到属性名称。  
  
 添加属性向导将所需的行添加到.idl 文件。 它还添加了`Get`和`Put`函数原型到 PolyCtl.h 中的类定义，并将空实现添加到 PolyCtl.cpp。 你可以通过打开 PolyCtl.cpp 并寻找函数检查这`get_Sides`和`put_Sides`。  
  
 虽然此时您已设置和检索属性的主干函数，它需要要存储的位置。 将创建一个变量以存储属性，并相应地更新函数。  
  
#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>若要创建一个变量以存储属性，并更新 put 和 get 方法  
  
1.  从解决方案资源管理器，打开 PolyCtl.h 并添加以下代码行后的定义`m_clrFillColor`:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  设置的默认值`m_nSides`。 请通过将行添加到 PolyCtl.h 中的构造函数中形成一个三角形默认值：  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  实现`Get`和`Put`方法。 `get_Sides`和`put_Sides`已添加到 PolyCtl.h 函数声明。 有关 PolyCtl.cpp 中的代码替换`get_Sides`和`put_Sides`替换为以下代码：  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 `get_Sides`方法返回的当前值`Sides`属性通过`pVal`指针。 在`put_Sides`方法，该代码可确保设置用户`Sides`为可接受值的属性。 最小值必须为 2，并且由于的点数组将用于每一侧，100 的最大值为合理的极限。  
  
 你现在具有一个名为属性`Sides`。 在下一步的步骤中，你将更改绘图代码以使用它。  
  
 [返回到步骤 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124;[到步骤 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## <a name="see-also"></a>另请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)

