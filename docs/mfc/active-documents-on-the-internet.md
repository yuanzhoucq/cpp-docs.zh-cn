---
title: Internet 上的活动文档 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], creating
- application wizards [MFC], active documents
- active documents [MFC], programming steps
- application wizards [MFC]
- active documents [MFC], using application wizards
ms.assetid: a46bd8a0-e27a-4116-b1bf-dacdb7ae78d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a18b84b30445060631589e72f6c158ea9b3626f0
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930883"
---
# <a name="active-documents-on-the-internet"></a>Internet 上的活动文档
活动文档提供传统嵌入对象的扩展。 活动文档可以是多页，并将显示在整个工作区。 它们执行传统的菜单协商，就地，以及在服务器应用程序中打开的窗口可以进行编辑。 而不是显示为通过阴影边框括起来的一个小矩形，活动文档是全帧和始终处于就地活动状态。  
  
 活动文档可以查看如 Microsoft Office 活页夹中，使您能够创建不同的文档类型，如 Excel、 Word、 组成的复合文档容器中，你的自定义文档类型，其中的每一个都可以编辑全帧。 活动文档还可以在 Microsoft Internet Explorer 中，这是活动文档容器之类的浏览器中显示。  
  
 **活动文档的优点包括：**  
  
-   文档可以查看在整个客户端窗口中的全帧。  
  
-   可以在一个单独的应用程序窗口中打开文档。  
  
     若要打开文档，帮助应用程序必须存在于客户端，或之前运行该应用程序可以单独下载。 可以编写一个查看器来提供有限的功能 （Word、 PowerPoint 和 Excel 为其文档中提供的查看者）。 完整版本的应用程序可以提供完全的编辑支持。  
  
-   文档是始终处于就地活动状态。  
  
-   可以将调用从容器的菜单命令路由到您的文档。  
  
-   可以在 Web 浏览器中查看文档。 这提供了你的文档和其他 Web 页之间的无缝集成。  
  
     用户可以浏览 HTML 网页，然后 Excel 电子表格，然后编写使用 MFC 的文档为和支持活动文档。 用户可以导航使用熟悉的 Web 界面，作为无缝之间的菜单和 HTML 页、 Excel 和应用程序的文档的视图的浏览器开关。  
  
-   所有应用程序的常见帧中显示。  
  
## <a name="requirements-for-active-documents"></a>活动文档需求  
 下表中列出的接口包括所需的嵌入服务器接口和特定于活动文档的某些新接口。 MFC 提供了大部分这些接口中的默认实现[COleServerDoc](../mfc/reference/coleserverdoc-class.md)类。  
  
|一个文档...|实现这些接口|  
|-------------------------|---------------------------------|  
|使用复合文件作为存储机制。|`IPersistStorage`。|  
|支持活动文档，包括从文件创建的基础嵌入功能。|`IPersistFile`、`IOleObject` 和 `IDataObject`。|  
|支持就地激活。|`IOleInPlaceObject` 和`IOleInPlaceActiveObject`(使用容器的`IOleInPlaceSite`和`IOleInPlaceFrame`接口)。|  
|支持涉及这些新的接口的活动文档扩展。 有些接口是可选的。|`IOleDocument`、`IOleDocumentView`、`IOleCommandTarget` 和 `IPrint`。|  
  
 MFC 提供支持，用于扩展现有嵌入的服务器支持添加到活动文档。  
  
## <a name="add-active-document-support-to-a-new-application"></a>将活动文档支持添加到新的应用程序  
 创建新的应用程序与活动文档支持： 在 MFC 应用程序向导，请在**复合文档支持**页上，在"选择的复合文档支持"下选择**完全服务器**或**容器/完全服务器**，并在"选择其他选项"下，选中的复选框**活动文档服务器**。  
  
##  <a name="_core_convert_an_existing_mfc_in.2d.process_server_to_an_activex_document_server"></a> 将现有 MFC 进程内服务器转换到活动文档服务器  
 如果你的应用程序创建的 Visual c + + 4.2 版之前的版本，并且已在进程服务器，你可以通过更改以下类中添加活动文档支持：  
  
|类类型|以前派生自|更改为派生自|  
|----------------|---------------------------|---------------------------|  
|就地框架|`COleIPFrameWnd`|`COleDocIPFrameWnd`|  
|项|`COleServerItem`|`CDocObjectServerItem`|  
  
 你还将更改在注册表中，输入信息的方式，并进行一些其他更改。 如果你的应用程序当前不具有任何 COM 组件支持，你可以通过运行应用程序向导并与你现有的应用程序集成 COM 组件特有的代码中添加服务器支持。  
  
## <a name="see-also"></a>请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)

