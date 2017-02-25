---
title: "MFC ActiveX 控件：方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC ActiveX 控件：方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控件激发事件通信在自身及其控件容器之间。  容器还可以与控件进行通信通过方法和属性。  方法也调用函数。  
  
 方法和属性提供的导出的接口供其他应用程序使用的数据，如的自动化客户程序和 ActiveX 控件容器。  有关 ActiveX 控件属性的更多信息，请参见知识库文章 [MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)。  
  
 方法非常相似在使用中并且打算为 C.C\+\+ 类的成员函数。  具有控件可以执行方法的两种类型：常用和自定义。  类似于常用事件，常用方法是 [COleControl](../mfc/reference/colecontrol-class.md) 提供的实现的方法。  有关常用方法的更多信息，请参见知识库文章 [MFC ActiveX 控件：添加常用方法](../mfc/mfc-activex-controls-adding-stock-methods.md)。  自定义方法，定义由开发人员，允许控件的其他自定义项。  有关更多信息，请参见知识库文章 [MFC ActiveX 控件：添加自定义方法](../mfc/mfc-activex-controls-adding-custom-methods.md)。  
  
 Microsoft 基础类库 \(MFC\) 实现允许控件支持和库存自定义方法的机制。  第一部分是类 `COleControl`。  从 `CWnd`派生，`COleControl` 成员函数支持的所有 ActiveX 控件共有的常用方法。  此机制的第二部分是计划映射。  计划映射与消息映射；但是，不是消息标识映射到 Windows 的函数，计划映射映射虚成员函数为 IDS IDispatch。  
  
 为了能够正确支持的控件的各种方法，其类必须声明计划映射。  这是在控件类标题中的下列代码行 \(完成。H\) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/CPP/mfc-activex-controls-methods_1.h)]  
  
 映射计划的主要目的生成外部调用方使用的方法名称 \(例如容器\) 和实现方法控件类的成员函数之间的关系。  在计划映射后声明，在控件的实现 \(.cpp\) 文件所定义。  以下代码行定义计划映射：  
  
 [!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/CPP/mfc-activex-controls-methods_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/CPP/mfc-activex-controls-methods_3.cpp)]  
  
 如果将使用 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md) 创建项目，这些行自动添加了。  如果未使用 MFC ActiveX 控件向导，您必须手动添加这些行。  
  
 下列文章详细讨论方法：  
  
-   [MFC ActiveX 控件：添加常用方法](../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [MFC ActiveX 控件：添加自定义方法](../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [MFC ActiveX 控件：从方法返回的错误代码](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)