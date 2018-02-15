---
title: "CSession 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
dev_langs:
- C++
helpviewer_keywords:
- CSession class
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3402255bbbfc8e66a55654d91434fa60680a80a3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="csession-class"></a>CSession 类
表示单个数据库访问会话。  
  
## <a name="syntax"></a>语法

```cpp
class CSession  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[中止](../../data/oledb/csession-abort.md)|取消（终止）事务。|  
|[关闭](../../data/oledb/csession-close.md)|关闭会话。|  
|[Commit](../../data/oledb/csession-commit.md)|提交事务。|  
|[GetTransactionInfo](../../data/oledb/csession-gettransactioninfo.md)|返回有关事务的信息。|  
|[打开](../../data/oledb/csession-open.md)|为数据源对象打开新会话。|  
|[StartTransaction](../../data/oledb/csession-starttransaction.md)|开始此会话的新事务。|  
  
## <a name="remarks"></a>备注  
 一个或多个会话可以与每个提供程序连接 （数据源），表示关联[CDataSource](../../data/oledb/cdatasource-class.md)对象。 若要创建一个新`CSession`为`CDataSource`，调用[csession:: Open](../../data/oledb/csession-open.md)。 为了开始数据库事务，`CSession` 提供了 `StartTransaction` 方法。 事务启动后，你可以提交到该使用**提交**方法，或取消它使用**中止**方法。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CatDB](../../visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)