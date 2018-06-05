---
title: 实现接口 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 309ae9dc576f93574836ab4916e87c5232b37a6c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332762"
---
# <a name="implementing-an-interface-visual-c"></a>实现接口 (Visual C++)
要实现接口，必须将项目创建为 ATL COM 应用程序或包含 ATL 支持的 MFC 应用程序。 可使用 [ATL 项目向导](../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[将 ATL 对象添加到 MFC 应用程序](../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。  
  
 创建项目后，要实现接口，必须首先添加 ATL 对象。 有关将对象添加到 ATL 项目的向导列表，请参阅[将对象和控件添加到 ATL 项目](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
> [!NOTE]
>  向导不支持 ATL 对话框、使用 ATL 的 XML Web 服务、性能对象或性能计数器。  
  
 如果[添加 ATL 控件](../atl/reference/adding-an-atl-control.md)，则可指定是否实现在该向导的[接口](../atl/reference/interfaces-atl-control-wizard.md)页上列出并在 atlcom.h 中定义的默认接口。  
  
 添加对象或控件后，可使用实现接口向导来实现位于任何可用类型库中的其他接口。  
  
 如果要添加新接口，则必须手动将其添加到项目的 .idl 文件中。 有关详细信息，请参阅[在 ATL 项目中添加新接口](../atl/reference/adding-a-new-interface-in-an-atl-project.md)。  
  
### <a name="to-implement-an-interface"></a>实现接口  
  
1.  在类视图中，右键单击 ATL 对象的类名。  
  
2.  单击快捷菜单中的“添加”，然后单击“实现接口”以显示[实现接口向导](../ide/implement-interface-wizard.md)。  
  
3.  从适当的类型库中选择要实现的接口，然后单击“完成”。  
  
4.  在类视图中，展开对象的基项和接口节点以查看已实现的接口，然后展开接口节点以查看其可用属性、方法和事件。  
  
    > [!NOTE]
    >  还可使用[对象浏览器](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470)检查接口的成员。  
  
## <a name="see-also"></a>请参阅  
 [创建 COM 接口](../ide/creating-a-com-interface-visual-cpp.md)   
 [编辑 COM 接口](../ide/editing-a-com-interface.md)