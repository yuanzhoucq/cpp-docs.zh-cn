---
title: "CCreateContext Structure | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCreateContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCreateContext structure"
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCreateContext Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

框架使用 `CCreateContext` 结构，在创建与文档框架窗口和视图时。  
  
## 语法  
  
```  
struct CCreateContext  
```  
  
## 备注  
 `CCreateContext` 是结构，并没有基类。  
  
 在创建窗口时，此结构的值中的信息连接文档的元素到其数据视图。  如果重写创建过程中，您只需 `CCreateContext`。  
  
 `CCreateContext` 结构包含指向文档、框架窗口、视图和文档模板。  它还包含标识视图的类型创建的指向 `CRuntimeClass`。  运行时选件类信息和当前文件指针使用动态创建新视图。  下表建议如何以及何时可以使用每个 `CCreateContext` 成员:  
  
|成员|类型|将针对|  
|--------|--------|---------|  
|`m_pNewViewClass`|`CRuntimeClass*`|创建的新视图的`CRuntimeClass`。|  
|`m_pCurrentDoc`|`CDocument*`|现有文档与新的视图。|  
|`m_pNewDocTemplate`|`CDocTemplate*`|文档模板与新的MDI框架窗口的创建。|  
|`m_pLastView`|`CView*`|附加视图进行建模的原始视图中，在拆分窗口视图中创建或第二个视图的创建文档中的。|  
|`m_pCurrentFrame`|`CFrameWnd*`|其他框架窗口进行建模的框架窗口，在第二个框架窗口中创建文档中的。|  
  
 当文档模板创建文档及其关联的元素时，它将验证 `CCreateContext` 结构中存储的信息。  例如，不应使用不存在创建视图文档。  
  
> [!NOTE]
>  所有在 `CCreateContext` 的指针是可选的，可以为 `NULL`，如果未指定或未知。  
  
 功能下面列出的“并查看的成员使用`CCreateContext` ”。如果您计划中重写这些属性，请参考这些函数的声明特定的信息。  
  
 这是一些通用准则:  
  
-   当通过，因为windows创建的参数，在 `CWnd::Create`，`CFrameWnd::Create`和 `CFrameWnd::LoadFrame`，创建上下文指定应连接的窗口。  对于大多数窗口，整个结构是可选的，并且 `NULL` 指针可以通过。  
  
-   对于可重写的成员函数，例如 `CFrameWnd::OnCreateClient`，`CCreateContext` 参数是可选的。  
  
-   对于视图创建涉及的成员函数时，必须提供足够的信息来创建视图。  例如，在拆分窗口的第一个视图，必须提供视图选件类信息，并且当前文件。  
  
 通常，因此，如果使用框架默认，您可以忽略 `CCreateContext`。  如果尝试更高级的修改，Microsoft基础类库选件源代码或示例程序，例如VIEWEX中，将引导您完成。  如果忘记一个必选参数，结构断言将告知您要忘记了。  
  
 有关 `CCreateContext`的更多信息，请参见MFC示例 [VIEWEX](../../top/visual-cpp-samples.md)。  
  
## 要求  
 **标头:** afxext.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../Topic/CFrameWnd::Create.md)   
 [CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md)   
 [CFrameWnd::OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md)   
 [CSplitterWnd::Create](../Topic/CSplitterWnd::Create.md)   
 [CSplitterWnd::CreateView](../Topic/CSplitterWnd::CreateView.md)   
 [CWnd::Create](../Topic/CWnd::Create.md)