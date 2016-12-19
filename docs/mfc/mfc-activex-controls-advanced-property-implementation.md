---
title: "MFC ActiveX 控件：高级属性实现 | Microsoft Docs"
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
  - "MFC ActiveX 控件, 错误代码"
  - "MFC ActiveX 控件, 属性"
  - "属性 [MFC], ActiveX 控件"
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：高级属性实现
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文在 ActiveX 控件相关主题介绍实现高级属性：  
  
-   [只读和只写属性。](#_core_read2donly_and_write2donly_properties)  
  
-   [从属性中返回错误代码](#_core_returning_error_codes_from_a_property)  
  
##  <a name="_core_read2donly_and_write2donly_properties"></a> 只读和只写属性。  
 添加属性向导提供一个快速、更简单的方法实现控件的只读或只写属性。  
  
#### 实现一只读或只写属性  
  
1.  加载控件的项目。  
  
2.  在"类视图，展开控件的库节点。  
  
3.  右击控件 \(库节点的第二个节点接口节点\) 打开快捷菜单。  
  
4.  从快捷菜单中单击 **添加**，然后单击 **添加属性**。  
  
     这会打开 [添加属性向导](../ide/names-add-property-wizard.md)。  
  
5.  在 **属性名** 框，键入属性的名称。  
  
6.  对于 **Implementation Type**，单击 **Get\/Set Methods**。  
  
7.  在 **属性类型** 框中，选择属性的适当类型。  
  
8.  如果需要一只读属性，请清除集合函数名称。  如果需要一只写属性，请清除获取函数名。  
  
9. 单击**“完成”**。  
  
 此时，"添加属性向导替换常规设置或获取函数位置插入在计划映射项的函数 `SetNotSupported` 或 `GetNotSupported`。  
  
 如果要更改现有属性的只读或只写，可以手动编辑计划映射并从控件类中移除不必要的设置或获取函数。  
  
 如果希望属性按条件只读或只写 \(例如，控件处于特定模式，只有运行\)，只要适用就可以提供设置或获取函数，用作常规，并调用 `SetNotSupported` 或 `GetNotSupported` 函数。  例如：  
  
 [!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-property-implementation_1.cpp)]  
  
 如果是 `m_bReadOnlyMode` 数据成员 **TRUE**，此代码示例改为调用 `SetNotSupported`。  如果 **FALSE**，随后的属性设置为新值。  
  
##  <a name="_core_returning_error_codes_from_a_property"></a> 从属性返回的错误代码  
 指示发生错误，如果尝试获取或设置属性，请使用 `COleControl::ThrowError` 函数，它采用 `SCODE` \(状态代码\) 作为参数。  可以使用预定义的 `SCODE` 还是定义一个拥有。  有关预定义的 `SCODE`s 和指令列表自定义的 `SCODE`，请参见在 ActiveX 控件的文章 [在 ActiveX 控件中的错误处理](../mfc/mfc-activex-controls-advanced-topics.md) :高级主题。  
  
 帮助程序函数。常见预定义的 `SCODE`。最存在，如 [COleControl::SetNotSupported](../Topic/COleControl::SetNotSupported.md)[COleControl::GetNotSupported](../Topic/COleControl::GetNotSupported.md)[COleControl::SetNotPermitted](../Topic/COleControl::SetNotPermitted.md)、和。  
  
> [!NOTE]
>  `ThrowError` 被视为是只能作为返回错误的方法从的属性获取或设置函数或自动化方法内。  这是仅有的时间相应的异常处理程序会存在于堆栈。  
  
 有关在代码的其他区域的异常报告的更多信息，请参见 [COleControl::FireError](../Topic/COleControl::FireError.md) 和节中的 [在 ActiveX 控件中的错误处理](../mfc/mfc-activex-controls-advanced-topics.md) 文章 ActiveX 控件：高级主题。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)