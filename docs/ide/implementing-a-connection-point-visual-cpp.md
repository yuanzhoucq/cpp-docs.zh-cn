---
title: "实现连接点 (Visual C++) | Microsoft Docs"
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
  - "连接点 [C++], 实现"
  - "实现连接点向导 [C++]"
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 实现连接点 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为使用“实现连接点向导”实现连接点，必须已创建了作为 ATL COM 应用程序或包含 ATL 支持的 MFC 应用程序的项目。  可使用 [ATL 项目向导](../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或者[向 MFC 应用程序项目添加 ATL 对象](../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。  
  
> [!NOTE]
>  有关为 MFC 项目实现连接点的信息，请参见[“连接点”](../mfc/connection-points.md)。  
  
 创建项目后，要实现连接点，必须首先添加 ATL 对象。  有关向 ATL 项目添加对象的向导列表，请参见[向 ATL 项目添加对象和控件](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
> [!NOTE]
>  向导不支持 ATL 对话框、用 ATL Server 创建的 XML Web services、性能对象或性能计数器。  
  
 可连接对象（即源）可以为它的每个输出接口公开连接点。  每个输出接口可由客户端在对象（即接收器）上实现。  有关更多信息，请参见 [ATL 连接点](../atl/atl-connection-points.md)。  
  
### 实现连接点  
  
1.  在类视图中，右击 ATL 对象的类名。  
  
2.  从快捷菜单中单击“添加”，然后单击“添加连接点”显示[实现连接点向导](../ide/implement-connection-point-wizard.md)。  
  
3.  选择要从适当的类型库实现的连接点接口并单击“完成”。  
  
4.  在类视图中，检查为每个连接点创建的代理类。  这些类显示为 CProxy*InterfaceName*\<T\> 并从 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 导出。  
  
5.  双击连接点类以显示连接点类的定义。  
  
    -   如果实现自己项目的接口的连接点，显示下列定义  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         如果实现本地接口，则方法和属性显示在类体中。  
  
    -   如果实现另一个接口的连接点，则定义包括该接口的方法，并且每个方法都带 `Fire_` 前缀。  
  
## 请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Adding Connection Points to an Object](../atl/adding-connection-points-to-an-object.md)