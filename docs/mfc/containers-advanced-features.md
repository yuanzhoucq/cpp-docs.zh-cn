---
title: "容器：高级功能 | Microsoft Docs"
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
  - "容器/服务器应用程序 [C++]"
  - "容器 [C++], 高级功能"
  - "容器 [C++], 容器应用程序"
  - "容器 [C++], 链接到嵌入的 OLE 对象"
  - "嵌入对象 [C++]"
  - "链接 [C++], 到嵌入的 OLE 对象"
  - "OLE 容器, 高级功能"
  - "OLE 控件, 容器"
  - "服务器/容器应用程序"
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 容器：高级功能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文描述所需步骤中合并选项高级功能到现有的容器应用程序中。  这些特性包括：  
  
-   [应用程序既是容器也是服务器](#_core_creating_a_container.2f.server_application)  
  
-   [OLE 链接到一个潜入的对象](#_core_links_to_embedded_objects)  
  
##  <a name="_core_creating_a_container.2f.server_application"></a> 创建一个容器\/服务器应用程序  
 服务器\/容器应用程序行为既是容器也是服务器。  对于Windows，Microsoft Word 是此一个示例。  您可以将Word for Windows文档嵌入到其他应用程序，也可以在 Word for Windows 文档中嵌入条目。  修改容器应用程序进程既是容器也是完整服务器 \(不能创建容器 \/miniserver组合应用程序\) 类似于创建完全服务器进程。  
  
 文章 [服务器：实现服务器](../mfc/servers-implementing-a-server.md) 列出很多所需的任务实现服务器应用程序。  如果将容器应用程序转换到容器\/服务器应用程序，则需要执行一些相同任务，添加代码到该容器。  下面列出了重要考虑的事情：  
  
-   由应用程序向导创建的已经初始化 OLE 子系统的容器代码。  不需要为该支持更改或添加任意东西。  
  
-   无论何时文本类的基类是 `COleDocument`，将基类更改为 `COleServerDoc`。  
  
-   当服务器用于适当编辑时，请重写 `COleClientItem::CanActivate` 以避免适当编辑条目。  
  
     例如，MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md) 已经嵌入由容器\/服务器应用程序创建的条目中。  您打开 OCLIENT 应用程序，适当编辑由容器\/服务器应用程序创建的项目。  当编辑应用程序的项时，决定要嵌入由 MFC OLE 示例 [HIERSVR](../top/visual-cpp-samples.md) 创建的项。  为此，不能使用就地激活。  必须完全打开 HIERSVR 来激活此项。  因为 Microsoft 基础类库不支持 OLE 功能，重写 `COleClientItem::CanActivate` 可以检查此情况并阻止应用程序的运行时错误。  
  
 如果创建新应用程序并想让它作为容器\/服务器应用程序函数，选择在应用程序向导 OLE 选项对话框中的选项并且此支持将自动创建。  有关详细信息，请参阅文章 [概述：创建 ActiveX 控件容器](../mfc/reference/creating-an-mfc-activex-control-container.md)。  有关 MFC 示例的信息，请参阅 MFC 示例。  
  
 注意不能将 MDI 应用程序插入到其本身。  容器是\/服务器的应用程序不能插入到其本身，除非它是 SDI 应用程序。  
  
##  <a name="_core_links_to_embedded_objects"></a> 链接到嵌入的对象  
 该链接嵌入对象功能使用户能够创建OLE链接到你的容器应用程序中嵌入对象的文档。  例如，在文字处理程序中创建包含嵌入的电子表格的文档。  如果应用程序支持连接到嵌入的对象，则可粘贴链接到在文字处理器的文档包含的电子表格。  此功能允许应用程序使用在电子表格包含的信息，而不必知道问字处理器最初何处获得它。  
  
#### 链接到应用程序中的嵌入对象  
  
1.  从 `COleLinkingDoc` 而不是 `COleDocument` 派生文档类。  
  
2.  通过使用包含 OLE 开发工具类 ID 生成器，为应用程序创建 OLE 类 ID \(**CLSID**\) 。  
  
3.  用 OLE 注册应用程序。  
  
4.  创建一个 `COleTemplateServer` 对象作为应用程序类的成员。  
  
5.  在应用程序类的 `InitInstance` 成员函数中，执行以下操作：  
  
    -   通过调用对象的 `ConnectTemplate` 成员函数连接 `COleTemplateServer` 对象到文档模板。  
  
    -   调用 **COleTemplateServer::RegisterAll** 成员函数来注册与 OLE 系统的所有类的对象。  
  
    -   调用 `COleTemplateServer::UpdateRegistry`。  如果应用程序未启动使用“\/Embedded”开关， `UpdateRegistry` 的唯一参数应该为 `OAT_CONTAINER`。  这将作为可支持连接到嵌入对象的容器注册应用程序。  
  
         如果启动应用程序“”开关 \/Embedded，则不应显示其主窗口，与服务器应用类似。  
  
 MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md) 实现此功能。  有关如何实现此方法的示例，请参阅本示例应用程序 OCLIENT.CPP 文件中的 `InitInstance` 函数。  
  
## 请参阅  
 [容器](../mfc/containers.md)   
 [服务器](../mfc/servers.md)