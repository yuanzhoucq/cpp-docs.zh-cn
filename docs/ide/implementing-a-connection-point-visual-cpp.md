---
title: 实现连接点 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b75bf145da401ad9889353a1e65448831c602c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328342"
---
# <a name="implementing-a-connection-point-visual-c"></a>实现连接点 (Visual C++)
若要使用实现连接点向导实现连接点，则必须将项目创建为 ATL COM 应用程序或包含 ATL 支持的 MFC 应用程序。 可使用 [ATL 项目向导](../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[将 ATL 对象添加到 MFC 应用程序](../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。  
  
> [!NOTE]
>  有关实现 MFC 项目的连接点的信息，请参阅[连接点](../mfc/connection-points.md)。  
  
 创建项目后，要实现连接点，必须首先添加 ATL 对象。 有关将对象添加到 ATL 项目的向导列表，请参阅[将对象和控件添加到 ATL 项目](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
> [!NOTE]
>  向导不支持 ATL 对话框，使用 ATL 服务器创建的 XML Web 服务、性能对象或性能计数器。  
  
 可连接对象（即，源）可以为其每个传出接口公开连接点。 每个传出接口都可以由对象（即，接收器）上的客户端实现。 有关详细信息，请参阅 [ATL 连接点](../atl/atl-connection-points.md)。  
  
### <a name="to-implement-a-connection-point"></a>实现连接点  
  
1.  在类视图中，右键单击 ATL 对象的类名。  
  
2.  从快捷菜单单击“添加”，然后单击“添加连接点”，显示[实现连接点向导](../ide/implement-connection-point-wizard.md)。  
  
3.  从适当的类型库中选择要实现的连接点接口，然后单击“完成”。  
  
4.  在类视图中，检查为每个连接点创建的代理类。 类显示为 CProxyInterfaceName\<T>，且派生自 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)。  
  
5.  双击连接点类，显示连接点类的定义。  
  
    -   如果为自己的项目接口实现连接点，则出现以下定义  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         如果实现本地接口，则在类正文中出现方法和属性。  
  
    -   如果实现其他接口的连接点，则定义包括接口的方法，每个方法前都为 `Fire_`。  
  
## <a name="see-also"></a>请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [将连接点添加到对象](../atl/adding-connection-points-to-an-object.md)