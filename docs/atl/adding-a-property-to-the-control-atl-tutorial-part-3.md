---
title: "向控件中添加属性（ATL 教程，第 3 部分） | Microsoft Docs"
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
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 向控件中添加属性（ATL 教程，第 3 部分）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`IPolyCtl` 是包含控件的自定义方法和属性的接口，因此，您将属性添加到它。  
  
### 使用"添加属性向导"，"添加属性  
  
1.  在选件类视图"中，展开多边形分支。  
  
2.  右击IPolyCtl。  
  
3.  在快捷菜单上，单击 **添加**，然后单击 **添加属性**。  
  
     添加属性向导将显示。  
  
4.  在下拉列表属性类型，选择 `SHORT`。  
  
5.  键入 `端` 作为 **属性名。**  
  
6.  单击完成的 **完成** 添加特性。  
  
 当您将该属性设置为生成.idl文件的接口\)时，MIDL \(过程定义检索其值的 `Get` 方法和设置的新值的 `Put` 方法。  方法是通过预置 `put_` 和 `get_` 命名于属性名称。  
  
 添加属性向导添加必要的行添加到.idl文件。  它还添加 `Get` 和 `Put` 函数原型到PolyCtl.h的类定义并添加一个空实现。PolyCtl.cpp。  可以通过打开PolyCtl.cpp和查找功能检查此 `get_Sides` 和 `put_Sides`。  
  
 尽管您现在具有检索摘要的功能设置和属性，需要一个位置来存储它。  您将创建一个变量以存储属性并相应地更新功能。  
  
#### 创建变量存储属性并更新的放置和访问方法  
  
1.  从解决方案资源管理器中，打开PolyCtl.h和在 `m_clrFillColor`的定义之后添加下面的行:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/CPP/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  设置 `m_nSides`的默认值。  通过添加行进行默认形状一个三角形到PolyCtl.h的构造函数:  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/CPP/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  实现 `Get` 和 `Put` 方法。  `get_Sides` 和 `put_Sides` 函数声明添加到PolyCtl.h。  用下面的代码替换该PolyCtl.cpp `get_Sides` 的和 `put_Sides` 的代码:  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/CPP/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 `get_Sides` 方法通过 `pVal` 指针返回 `Sides` 属性的当前值。  在 `put_Sides` 方法中，代码确保用户设置 `Sides` 属性设置为一个接受的值。  最小必须为2，因为一系列点为每一端，100使用是最大值的合理的限制。  
  
 现在您有调用 `Sides`的属性。  在下一步，您将更改绘图代码使用它。  
  
 [返回第2步](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [在到步骤4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## 请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)