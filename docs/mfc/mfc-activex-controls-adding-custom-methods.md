---
title: "MFC ActiveX 控件：添加自定义方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控件, 方法"
  - "PtInCircle 自定义方法"
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：添加自定义方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自定义方法与常用方法有所不同它们不会被 `COleControl`中实现。  必须提供您添加到控件上的每个自定义方法的实现。  
  
 ActiveX 控件用户可随时调用自定义方法以控件执行特定操作。  自定义计划映射方法的输入窗体是 `DISP_FUNCTION`。  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a> 添加使用添加方法向导的自定义方法  
 下面的过程演示添加自定义方法 PtInCircle 到 ActiveX 控件的主干代码。  确定 PtInCircle 坐标传递给控件是否在内部或外部的圆。  此相同过程也可添加其他自定义方法。  替换 PtInCircle 方法名称和参数重写自定义方法名称及其参数。  
  
> [!NOTE]
>  本示例使用源自文章事件的 `InCircle` 函数。  有关此函数的更多信息，请参见知识库文章 [MFC ActiveX 控件：添加自定义事件向 ActiveX 控件](../mfc/mfc-activex-controls-adding-custom-events.md)。  
  
#### 使用 Add 方法向导，将 PtInCircle 自定义方法  
  
1.  加载控件的项目。  
  
2.  在类视图中，展开控件的库节点。  
  
3.  右击控件的接口节点 \(库节点的第二个节点\) ，打开快捷菜单。  
  
4.  从快捷菜单中单击“添加”，然后单击“添加方法”。  
  
     这将打开"添加方法向导"  
  
5.  在**“方法名称”** 框中, 键入 `PtInCircle`。  
  
6.  在 **内部名称** 框中，为键入方法的内部函数的名称或使用默认值 \(在这种情况下，`PtInCircle`\)。  
  
7.  在 **返回类型** 框中，单击方法的返回类型的 **VARIANT\_BOOL**。  
  
8.  使用 **参数类型** 和 **参数名称**，控件添加一个名为 `xCoord` 的参数类型 \( **OLE\_XPOS\_PIXELS**\)。  
  
9. 使用 **参数类型** 和 **参数名称**，控件添加一个名为 `yCoord`  的参数类型 \( **OLE\_XPOS\_PIXELS**\)。  
  
10. 单击**“完成”**。  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a> 添加方法向导的更改自定义方法  
 当您将自定义方法时，添加方法向导对标题控件的类 \(这些更改。H\) 和实现 \(.cpp\) 文件。  下列代码行添加到控件标头类的声明计划映射（.H） 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 此代码声明计划方法处理程序调用 `PtInCircle`。  此函数可由使用外部名称 PtInCircle 的用户控件。  
  
 下列代码行添加到控件的 .idl 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 此行将 PtInCircle 方法特定 ID 号，在"添加方法向导方法的方法和位置，属性列出。  由于添加方法向导使用添加自定义方法，则该项会自动添加到项目的 .idl 文件。  
  
 此外，以下行位于控件类的实现 \(.cpp\) 文件，向控件添加的计划映射：  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 `DISP_FUNCTION` 宏映射方法 PtInCircle 该控件的处理程序函数，声明 `PtInCircle`，返回类型为 **VARIANT\_BOOL**，并声明类型传递 **VTS\_XPOS\_PIXELS** 和 **VTS\_YPOSPIXELS** 参数都为 `PtInCircle`。  
  
 最后，添加方法向导存根 \(stub\) 添加到函数 `CSampleCtrl::PtInCircle` 控件的实现 \(.cpp\) 文件的底部。  对于 `PtInCircle` 函数为以前指定，则必须修改为如下所示：  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [“类视图”和“对象浏览器”图标](../Topic/Class%20View%20and%20Object%20Browser%20Icons.md)