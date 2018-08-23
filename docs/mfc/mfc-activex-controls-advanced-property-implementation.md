---
title: MFC ActiveX 控件： 高级属性实现 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb3ba387d4b6fcca7b30cd360dff84b9da4302a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928359"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC ActiveX 控件：高级属性实现
本指南介绍了与实现高级的 ActiveX 控件中的属性相关的主题：  
  
-   [只读和只写属性](#_core_read2donly_and_write2donly_properties)  
  
-   [从属性返回错误代码](#_core_returning_error_codes_from_a_property)  
  
##  <a name="_core_read2donly_and_write2donly_properties"></a> 只读和只写属性  
 添加属性向导提供的快速而简单的方法来实现控件的只读或只写属性。  
  
#### <a name="to-implement-a-read-only-or-write-only-property"></a>若要实现只读或只写属性  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中，单击**添加**，然后单击**添加属性**。  
  
     这将打开[添加属性向导](../ide/names-add-property-wizard.md)。  
  
5.  在**属性名称**框中，键入你的属性的名称。  
  
6.  对于“实现类型” ，请单击“Get/Set 方法” 。  
  
7.  在**属性类型**框中，选择正确的类型的属性。  
  
8.  如果你想只读属性，则清除集函数名称。 如果你希望只写属性，，清除 Get 函数名称。  
  
9. 单击 **“完成”**。  
  
 添加属性向导执行此操作时，插入函数`SetNotSupported`或`GetNotSupported`代替常规的调度映射项中设置或获取函数。  
  
 如果你想要更改现有属性为只读或只写，你可以手动编辑调度映射，并从 control 类删除不必要的 Set 或 Get 函数。  
  
 如果你想要为有条件地只读或只写 （例如，仅当在特定的模式下运行你的控件时） 的属性，你可以提供 Set 或 Get 函数的正常工作，并调用`SetNotSupported`或`GetNotSupported`函数在适当的位置。 例如：  
  
 [!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]  
  
 此代码示例调用`SetNotSupported`如果`m_bReadOnlyMode`数据成员是**TRUE**。 如果**FALSE**，则该属性设置为新值。  
  
##  <a name="_core_returning_error_codes_from_a_property"></a> 从属性返回错误代码  
 若要指示错误发生时尝试获取或设置一个属性，使用`COleControl::ThrowError`函数，其将作为参数 SCODE （状态代码）。 你可以使用预定义的 SCODE 或定义你自己的一个。 预定义 SCODEs 和用于定义自定义 SCODEs 说明的列表，请参阅[ActiveX 控件中处理错误](../mfc/mfc-activex-controls-advanced-topics.md)中文章 ActiveX 控件： 高级主题。  
  
 存在帮助器函数的最常见的预定义 SCODEs，如[colecontrol:: Setnotsupported](../mfc/reference/colecontrol-class.md#setnotsupported)， [colecontrol:: Getnotsupported](../mfc/reference/colecontrol-class.md#getnotsupported)，和[COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
> [!NOTE]
>  `ThrowError` 用于返回属性的 Get 或 Set 从错误的一种方法只可用作函数或自动化方法。 这是适当异常处理程序将出现在堆栈上的唯一时间。  
  
 有关报告代码的其他区域中的异常的详细信息，请参阅[COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror)和节[ActiveX 控件中处理错误](../mfc/mfc-activex-controls-advanced-topics.md)中文章 ActiveX 控件： 高级主题。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件： 属性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控件： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 类](../mfc/reference/colecontrol-class.md)
