---
title: "在 Visual C++ 中使用 ActiveX 控件进行数据绑定 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], 数据绑定"
  - "绑定控件 [C++], ActiveX"
  - "控件 [C++], 数据绑定"
  - "数据绑定 [C++], ActiveX 控件"
  - "数据绑定控件 [C++], ActiveX"
ms.assetid: afe11d2b-eefe-43ce-958d-82d3d4dee158
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual C++ 中使用 ActiveX 控件进行数据绑定
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

数据绑定通过两种类型的 ActiveX 控件实现：数据控件和数据绑定控件。  
  
 **数据控件**  
 数据控件负责封装数据库查询和检索的行集合。  Microsoft 数据控件提供了由一系列循环访问数据的按钮组成的用户界面。  Visual C\+\+ 为数据控件提供了两种数据访问技术：[ADO 和 RDO](../../data/ado-rdo/data-access-ado-and-rdo.md)。  
  
> [!IMPORTANT]
>  ADO 和 RDO 数据控件是一种旧技术，早期版本的 Visual Studio 中发布了这些控件，但当前版本中不会提供它们。  要使用本部分中的信息，可能需要获得以前的版本，以获取相应的控件。  
  
 **数据绑定控件**  
 数据绑定控件负责显示数据。  数据绑定控件连接到数据控件以接收数据，并通过各种不同的用户界面显示数据。  Visual C\+\+ 应用程序还可以将变量绑定到数据绑定控件中的数据值集；请参见 [CWnd::BindProperty](../Topic/CWnd::BindProperty.md)。  
  
 有关数据绑定的更多信息，请参见：  
  
-   [MFC ActiveX 控件：在 ActiveX 控件中使用数据绑定](../../mfc/mfc-activex-controls-using-data-binding-in-an-activex-control.md)  
  
-   [数据访问：ADO 和 RDO](../../data/ado-rdo/data-access-ado-and-rdo.md)  
  
-   [ADO 数据绑定](../../data/ado-rdo/ado-databinding.md)  
  
-   [RDO 数据绑定](../../data/ado-rdo/rdo-databinding.md)  
  
-   [包装类](../../data/ado-rdo/wrapper-classes.md)  
  
-   [设置 ActiveX 控件的事件处理程序](../../data/ado-rdo/setting-event-handlers-on-activex-controls.md)  
  
-   [错误捕获](../../data/ado-rdo/error-trapping.md)  
  
-   [数据绑定的限制](../../data/ado-rdo/limitations-of-databinding.md)  
  
## 请参阅  
 [数据绑定控件（ADO 和 RDO）](../../data/ado-rdo/data-bound-controls-ado-and-rdo.md)