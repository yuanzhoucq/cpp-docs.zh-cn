---
title: 会话对象接口 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 957fe69b413496af46aa8e19afd45ee41e58b490
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081768"
---
# <a name="session-object-interfaces"></a>会话对象接口

下表显示了定义由 OLE DB 会话对象的必需和可选接口。  
  
|接口|是否必需？|实现的 OLE DB 模板？|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](/previous-versions/windows/desktop/ms709721)|强制|是|  
|[IOpenRowset](/previous-versions/windows/desktop/ms716946)|强制|是|  
|[ISessionProperties](/previous-versions/windows/desktop/ms713721)|强制|是|  
|[IAlterIndex](/previous-versions/windows/desktop/ms714943)|Optional|否|  
|[IAlterTable](/previous-versions/windows/desktop/ms719764)|Optional|否|  
|[IBindResource](/previous-versions/windows/desktop/ms714936)|Optional|否|  
|[ICreateRow](/previous-versions/windows/desktop/ms716832)|Optional|否|  
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625)|Optional|是|  
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)|Optional|是|  
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593)|Optional|否|  
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|Optional|是|  
|[ITableCreation](/previous-versions/windows/desktop/ms713639)|Optional|否|  
|[ITableDefinition](/previous-versions/windows/desktop/ms714277)|Optional|否|  
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947)|Optional|否|  
|[ITransaction](/previous-versions/windows/desktop/ms723053)|Optional|否|  
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071)|Optional|否|  
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893)|Optional|否|  
|[ITransactionObject](/previous-versions/windows/desktop/ms713659)|Optional|否|  
  
会话对象创建行集对象。 如果提供程序支持的命令，该会话还会创建命令对象 (`CCommand`，实现 OLE DB `TCommand`)。 命令对象实现`ICommand`接口并使用`ICommand::Execute`方法以在行集上执行命令下, 图中所示。  
  
![提供程序概念图](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>请参阅  

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)