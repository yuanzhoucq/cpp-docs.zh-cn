---
title: "实现接口 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 896ada2c46c68a794265e7344e9b7f7c7f91aebe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-an-interface-visual-c"></a>实现接口 (Visual C++)
若要实现接口，你必须创建一个项目作为 ATL COM 应用程序或 MFC 应用程序包含 ATL 支持。 你可以使用[ATL 项目向导](../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[ATL 对象添加到 MFC 应用程序](../mfc/reference/adding-atl-support-to-your-mfc-project.md)实现为 MFC 应用程序的 ATL 支持。  
  
 一旦你创建项目，来实现接口，您必须首先添加 ATL 对象。 请参阅[向 ATL 项目添加对象和控件](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)有关的对象添加到你的 ATL 项目向导的列表。  
  
> [!NOTE]
>  向导不支持 ATL 对话框，使用 ATL、 性能对象或性能计数器的 XML Web 服务。  
  
 如果你[添加 ATL 控件](../atl/reference/adding-an-atl-control.md)，你可以指定是否实现上列出的默认接口[接口](../atl/reference/interfaces-atl-control-wizard.md)的向导和了 atlcom.h 中定义的页。  
  
 一旦你已添加的对象或控件，可以实现其他接口，位于任何可用的类型库，使用实现接口向导。  
  
 如果在添加新接口，必须手动将其添加到项目的.idl 文件。 请参阅[ATL 项目中添加一个新接口](../atl/reference/adding-a-new-interface-in-an-atl-project.md)有关详细信息。  
  
### <a name="to-implement-an-interface"></a>若要实现接口  
  
1.  在类视图中，右键单击你的 ATL 对象的类名称。  
  
2.  单击**添加**从快捷菜单，然后单击**实现接口**以显示[实现接口向导](../ide/implement-interface-wizard.md)。  
  
3.  选择要实现接口从适当的类型库并单击**完成**。  
  
4.  在类视图中展开对象的基类和接口节点以查看已实现，并且然后展开接口的节点以查看其可用的属性、 方法和事件的接口。  
  
    > [!NOTE]
    >  你还可以使用[对象浏览器](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470)检查接口的成员。  
  
## <a name="see-also"></a>请参阅  
 [创建 COM 接口](../ide/creating-a-com-interface-visual-cpp.md)   
 [编辑 COM 接口](../ide/editing-a-com-interface.md)