---
title: "实现连接点 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ab065c78d8ea5d2de105abdc2fa651e05f9d1875
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-connection-point-visual-c"></a>实现连接点 (Visual C++)
若要实现连接点使用实现连接点向导，你必须创建一个项目作为 ATL COM 应用程序或 MFC 应用程序包含 ATL 支持。 你可以使用[ATL 项目向导](../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[ATL 对象添加到 MFC 应用程序](../mfc/reference/adding-atl-support-to-your-mfc-project.md)实现为 MFC 应用程序的 ATL 支持。  
  
> [!NOTE]
>  有关实现连接点的 MFC 项目的信息，请参阅[连接点](../mfc/connection-points.md)。  
  
 一旦你创建项目，来实现连接点，您必须首先添加 ATL 对象。 请参阅[向 ATL 项目添加对象和控件](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)有关的对象添加到你的 ATL 项目向导的列表。  
  
> [!NOTE]
>  向导不支持 ATL 对话框，使用 ATL Server、 性能对象或性能计数器创建 XML Web 服务。  
  
 可连接对象 （即，对源） 可以为每个其传出接口公开连接点。 每个输出接口可以实现客户端上的对象 （即，接收器）。 有关详细信息，请参阅[ATL 连接点](../atl/atl-connection-points.md)。  
  
### <a name="to-implement-a-connection-point"></a>若要实现连接点  
  
1.  在类视图中，右键单击你的 ATL 对象的类名称。  
  
2.  单击**添加**从快捷菜单，然后单击**添加连接点**以显示[实现连接点向导](../ide/implement-connection-point-wizard.md)。  
  
3.  选择要实现从适当的类型库并单击连接点接口**完成**。  
  
4.  在类视图中，检查创建的每个连接点的代理类。 类显示为 CProxy*InterfaceName*\<T >，并从派生[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)。  
  
5.  双击要显示的连接点的类定义的连接点类。  
  
    -   如果你实现自己的项目的接口的连接点，显示的以下定义  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         如果你实现了本地接口，方法和属性将出现在类正文中。  
  
    -   如果你实现另一个接口的连接点，则定义包括接口的方法，每个前面`Fire_`。  
  
## <a name="see-also"></a>请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [将连接点添加到对象](../atl/adding-connection-points-to-an-object.md)