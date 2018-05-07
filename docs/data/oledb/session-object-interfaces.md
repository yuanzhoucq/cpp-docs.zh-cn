---
title: 会话对象接口 |Microsoft 文档
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
ms.openlocfilehash: f591e62874bd6924dd60077b921bbfc67600af1c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="session-object-interfaces"></a>会话对象接口
下表显示为会话对象定义由 OLE DB 的必需和可选接口。  
  
|接口|是否必需？|实现的 OLE DB 模板？|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](https://msdn.microsoft.com/en-us/library/ms709721.aspx)|强制|是|  
|[IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx)|强制|是|  
|[ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx)|强制|是|  
|[IAlterIndex](https://msdn.microsoft.com/en-us/library/ms714943.aspx)|Optional|否|  
|[IAlterTable](https://msdn.microsoft.com/en-us/library/ms719764.aspx)|Optional|否|  
|[IBindResource](https://msdn.microsoft.com/en-us/library/ms714936.aspx)|Optional|否|  
|[ICreateRow](https://msdn.microsoft.com/en-us/library/ms716832.aspx)|Optional|否|  
|[IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx)|Optional|是|  
|[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)|Optional|是|  
|[IIndexDefinition](https://msdn.microsoft.com/en-us/library/ms711593.aspx)|Optional|否|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Optional|是|  
|[ITableCreation](https://msdn.microsoft.com/en-us/library/ms713639.aspx)|Optional|否|  
|[ITableDefinition](https://msdn.microsoft.com/en-us/library/ms714277.aspx)|Optional|否|  
|[ITableDefinitionWithConstraints](https://msdn.microsoft.com/en-us/library/ms720947.aspx)|Optional|否|  
|[ITransaction](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|Optional|否|  
|[ITransactionJoin](https://msdn.microsoft.com/en-us/library/ms718071.aspx)|Optional|否|  
|[ITransactionLocal](https://msdn.microsoft.com/en-us/library/ms714893.aspx)|Optional|否|  
|[ITransactionObject](https://msdn.microsoft.com/en-us/library/ms713659.aspx)|Optional|否|  
  
 会话对象创建一个行集对象。 如果提供程序支持命令，会话还会创建命令对象 (`CCommand`，实现 OLE DB **TCommand**)。 命令对象实现`ICommand`接口并使用`ICommand::Execute`方法在行集上执行命令下, 图中所示。  
  
 ![提供程序概念图](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)