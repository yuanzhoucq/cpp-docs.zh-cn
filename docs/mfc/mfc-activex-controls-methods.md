---
title: "MFC ActiveX 控件： 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e3b343b13118930612e4adfed4c33a65a9e7be8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-methods"></a>MFC ActiveX 控件：方法
ActiveX 控件，将引发事件本身和其控件容器之间进行通信。 容器还可以通信与控件，通过方法和属性。 方法也称为函数。  
  
 方法和属性的其他应用程序，如自动化客户端和 ActiveX 控件容器用于提供导出的接口。 ActiveX 控件属性的详细信息，请参阅文章[MFC ActiveX 控件： 属性](../mfc/mfc-activex-controls-properties.md)。  
  
 方法是在使用和用途类似于 c + + 类的成员函数。 有两种类型的你的控件可以实现的方法： 常用和自定义。 类似于常用事件，库存方法指的是那些为其[COleControl](../mfc/reference/colecontrol-class.md)提供的实现。 常用方法的详细信息，请参阅文章[MFC ActiveX 控件： 添加常用方法](../mfc/mfc-activex-controls-adding-stock-methods.md)。 由开发人员定义的自定义方法允许其他自定义控件。 有关详细信息，请参阅文章[MFC ActiveX 控件： 添加自定义方法](../mfc/mfc-activex-controls-adding-custom-methods.md)。  
  
 Microsoft 基础类库 (MFC) 实现一种机制，允许你控制，以支持 stock 和自定义方法。 第一部分是类`COleControl`。 派生自`CWnd`，`COleControl`成员函数支持共有的所有 ActiveX 控件的常用方法。 此机制的第二部分是调度映射。 调度映射是类似于消息映射;但是，而不是将一个函数映射到 Windows 消息 ID，调度映射到 IDispatch ID 映射虚拟成员函数。  
  
 若要正确支持不同的方法的控件，其类必须声明调度映射。 这通过下面的代码位于控件类标头行实现 (。H） 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]  
  
 调度映射的主要用途是类的建立使用外部调用方 （如容器） 和控件的实现方法的成员函数的方法名称之间的关系。 声明调度映射后，它需要在控件的实现中定义 (。CPP) 文件。 下面的代码行定义的调度映射：  
  
 [!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]  
  
 如果你使用[MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)以创建该项目，这些行已自动添加。 如果未使用 MFC ActiveX 控件向导，您必须手动添加这些行。  
  
 以下文章介绍了详细信息中的方法：  
  
-   [MFC ActiveX 控件：添加常用方法](../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [MFC ActiveX 控件：添加自定义方法](../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [MFC ActiveX 控件：从方法中返回错误代码](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

