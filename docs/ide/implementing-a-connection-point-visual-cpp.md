---
title: 实现连接点
ms.date: 05/14/2019
helpviewer_keywords:
- connection points [C++], implementing
- implement connection point wizard [C++]
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
ms.openlocfilehash: 8a75a5fbbabd20f4591e3a119c175d68cdfb1f90
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "66182597"
---
# <a name="implement-a-connection-point"></a>实现连接点

若要使用实现连接点向导实现连接点，则必须将项目创建为 ATL COM 应用程序或包含 ATL 支持的 MFC 应用程序。 可使用 [ATL 项目向导](../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[将 ATL 对象添加到 MFC 应用程序](../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现对 MFC 应用程序的 ATL 支持。

> [!NOTE]
> 有关实现 MFC 项目的连接点的信息，请参阅[连接点](../mfc/connection-points.md)。

创建项目后，要实现连接点，必须首先添加 ATL 对象。 有关将对象添加到 ATL 项目的向导列表，请参阅[将对象和控件添加到 ATL 项目](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。

> [!NOTE]
> 向导不支持 ATL 对话框，使用 ATL 服务器创建的 XML Web 服务、性能对象或性能计数器。

可连接对象（即源）可为其每个传出接口显示连接点。 每个传出接口都可以由对象（即，接收器）上的客户端实现。 有关详细信息，请参阅 [ATL 连接点](../atl/atl-connection-points.md)。

**实现连接点：**

1. 在类视图中，右键单击 ATL 对象的类名。

1. 从快捷菜单中选择“添加”，然后选择“添加连接点”，显示[实现连接点向导](#implement-connection-point-wizard)   。

1. 从适当的类型库中选择要实现的连接点接口，然后选择“完成”  。

1. 在类视图中，检查为每个连接点创建的代理类。 类显示为 CProxyInterfaceName\<T>，且派生自 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)  。

1. 双击连接点类，显示连接点类的定义。

   - 如果为自己的项目接口实现连接点，则出现以下定义：

     ```cpp
     template< class T >
     class CProxyInterfaceName :
     public IConnectionPointImpl< T, &IID_InterfaceName >
     {
     public:
     };
     ```

   - 如果实现本地接口，则在类正文中出现方法和属性。

   - 如果实现其他接口的连接点，则定义包括接口的方法，每个方法前都为 `Fire_`。

## <a name="in-this-section"></a>本节内容

- [实现连接点向导](#implement-connection-point-wizard)

## <a name="implement-connection-point-wizard"></a>实现连接点向导

本向导实现 COM 对象的连接点。 可连接对象（即源）可以为其自身接口或任何传出接口显示连接点。 MSVC 和 Windows 均提供具有传出接口的类型库。 每个传出接口都可以由对象（即，接收器）上的客户端实现。

有关详细信息，请参阅 [ATL 连接点](../atl/atl-connection-points.md)。

- **可用类型库**

  显示包含可实现连接点的接口定义的可用类型库。 选择省略号按钮，找到包含要使用的类型库的文件。

- **位置**

  显示“可用类型库”列表中当前选择的类型库的位置  。

- **接口**

  显示其定义包含在“可用类型库”框中当前选定的类型库中的接口  。

  |传输按钮|说明|
  |---------------------|-----------------|
  |**>**|将当前在“接口”列表中选择的接口名称添加到“实现连接点”列表中   。|
  |**>>**|将在“接口”列表中可用的所有接口名称添加到“实现连接点”列表中   。|
  |**\<**|删除当前在“实现连接点”列表中所选的接口名称  。|
  |**\<\<**|删除当前在“实现连接点”列表中列出的所有接口名称  。|

- **实现连接点**

  选择“完成”时显示实现其连接点的接口的名称  。
