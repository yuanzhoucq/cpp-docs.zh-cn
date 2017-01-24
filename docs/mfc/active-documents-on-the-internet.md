---
title: "Internet 上的活动文档 | Microsoft Docs"
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
  - "活动文档 [C++], 创建"
  - "活动文档 [C++], 编程步骤"
  - "活动文档 [C++], 使用应用程序向导"
  - "应用程序向导 [C++]"
  - "应用程序向导 [C++], 活动文档"
ms.assetid: a46bd8a0-e27a-4116-b1bf-dacdb7ae78d1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Internet 上的活动文档
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

活动文档提供给扩展传统嵌入对象。  活动文档在整个工作区可以多页和显示。  它们执行传统协商菜单，可以编辑的就地以及在的服务器应用一个打开。  除了显示，因为一个阴影框包围的小矩形中，对活动文档已满帧、以及总是处于就地活动状态。  
  
 活动文档 \(如 Microsoft Office 活页夹的容器，以提供一种创建复合排列文档与 Excel 的文档不同的类型，Word 和自定义文档类型，其中每个类型都是可编辑的完整框架。  活动文档在浏览器还显示如 Microsoft Internet Explorer，是活动文档容器。  
  
 **活动文档有条件包括：**  
  
-   文档可以是演示的完整框架，如整个客户端窗口。  
  
-   文档在单独的应用程序窗口中打开。  
  
     对于打开的文档，在应用程序运行之前，应用程序，帮助客户端上必须存在或单独下载。  浏览器可能编写提供功能有限 \(Word、PowerPoint 和 Excel 的文档的浏览器提供\)。  应用程序的完全版本可以提供完全支持编辑。  
  
-   文档始终处于就地活动状态。  
  
-   从容器调用的菜单命令可以发送到文档。  
  
-   文档在 Web 浏览器中显示。  这提供在文档和其他网页之间\) 的无缝集成。  
  
     可以浏览 HTML 网页，然后 Excel 电子表格，然后为您编写使用 MFC 支持针对活动的文档。  使用熟悉 Web 界面，用户可以导航，浏览器切换无缝在 HTML 页的菜单和视图之间，Excel 和应用程序的文档。  
  
-   所有应用程序都通用框架中显示。  
  
## 需要活动文档  
 表中列出的接口在包含一连接尚需要嵌入的服务器和若干新接口的特定于活动文档。  MFC 提供大多数在 [COleServerDoc](../mfc/reference/coleserverdoc-class.md) 类的这些接口提供默认实现。  
  
|文档的…|实现接口。|  
|----------|-----------|  
|使用复合文件作为存储机制。|`IPersistStorage`.|  
|支持 Active 文档基础的嵌入功能，包括 Create From File。|`IPersistFile`、`IOleObject` 和 `IDataObject`。|  
|支持就地激活|`IOleInPlaceObject` 和 `IOleInPlaceActiveObject` \(使用容器的 `IOleInPlaceSite` 和 **IOleInPlaceFrame** 接口\)。|  
|支持涉及这些新接口的扩展。活动文档  有些接口是可选的。|`IOleDocument`、`IOleDocumentView`、`IOleCommandTarget` 和 `IPrint`。|  
  
 MFC 为扩展的现有服务器支持嵌入的支持向活动文档。  
  
## 向新应用程序的活动文档支持  
 创建使用活动文档支持的新应用程序：在 MFC 应用程序向导，在 **复合文档支持** 页，的“SELECT 复合文档支持”下选择 **Full\-server** 或 **Container\/Full\-server**，并且，在“选择"附加选项”下选择 **活动文档服务器 \(A\)**的复选框。  
  
##  <a name="_core_convert_an_existing_mfc_in.2d.process_server_to_an_activex_document_server"></a> 转换现有 MFC 进程内服务器到活动文档服务器  
 如果应用程序使用 Visual C\+\+ 创建在 4.2 版之前版本并且已经是进程内服务器，则可以通过对以下类的更改添加活动文档支持：  
  
|类类型|以前从派生|更改派生|  
|---------|-----------|----------|  
|就地帧|`COleIPFrameWnd`|**COleDocIPFrameWnd**|  
|项|`COleServerItem`|`CDocObjectServerItem`|  
  
 也将更改信息在注册表输入，并使多其他更改。  如果当前应用程序没有 COM 组件支持，可以通过运行应用程序向导和集成与现有应用程序的 COM 组件的代码添加服务器支持。  
  
## 请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)