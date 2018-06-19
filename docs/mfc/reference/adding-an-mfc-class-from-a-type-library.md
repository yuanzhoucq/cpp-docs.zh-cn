---
title: 从类型库添加 MFC 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 349d06d7fecb82af64fbf2d3b2ebe54689b3b292
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355111"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>从类型库添加 MFC 类
使用此向导创建 MFC 类时从可用的类型库中的接口。 你可以添加到的 MFC 类[MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)、 [MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)，或[MFC ActiveX 控件](../../mfc/reference/creating-an-mfc-activex-control.md)。  
  
> [!NOTE]
>  不需要使用启用从类型库添加类的自动化创建 MFC 项目。  
  
 类型库包含由组件，定义其参数和返回类型以及方法公开的接口的二进制说明。 必须注册类型库，它才会显示在**可用的类型库**列表中从类型库向导添加类。 请参阅"在分布式 COM:: 类型库和语言集成"详细信息的 MSDN 库中。  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>若要从类型库添加 MFC 类  
  
1.  在**解决方案资源管理器**或[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，右键单击你想要将类添加的项目的名称。  
  
2.  从快捷菜单中，单击**添加**，然后单击**添加类**。  
  
3.  在[添加类](../../ide/add-class-dialog-box.md)对话框中，在模板窗格中，单击**类型库中的 MFC 类**，然后单击**打开**以显示[从类型库向导添加类](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 在向导中，你可以添加类型库中的多个类。 同样，你可以添加类从多个类型库在单个向导会话中。  
  
 该向导创建的 MFC 类，派生自[COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)，从所选的类型库添加每个接口。 `COleDispatchDriver` 实现 OLE 自动化的客户端。  
  
## <a name="see-also"></a>请参阅  
 [自动化客户端](../../mfc/automation-clients.md)   
 [自动化客户端：使用类型库](../../mfc/automation-clients-using-type-libraries.md)

