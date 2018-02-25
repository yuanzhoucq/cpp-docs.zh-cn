---
title: "IRowsetNotifyImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 43a71127512f679131cf767cfdc5147efe23e2ef
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl 类
实现并注册[IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)上使用者 （也称为"接收器"），以便它可以处理通知。  
  
## <a name="syntax"></a>语法

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[OnFieldChange](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|通知对列的值的任何更改的使用者。|  
|[OnRowChange](../../data/oledb/irowsetnotifyimpl-onrowchange.md)|通知使用者的第一个更改行或任何更改的影响到整行。|  
|[OnRowsetChange](../../data/oledb/irowsetnotifyimpl-onrowsetchange.md)|通知影响整个行集的任何更改的使用者。|  
  
## <a name="remarks"></a>备注  
 请参阅[接收通知](../../data/oledb/receiving-notifications.md)如何实现上使用者连接点接口。  
  
 `IRowsetNotifyImpl` 提供的虚拟实现`IRowsetNotify`，具有可实现的空功能`IRowsetNotify`方法[OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)， [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)，和[OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx). 如果在实现时，在从此类继承`IRowsetNotify`接口，你可以实现只有你需要的方法。 你还需要自行提供的其他方法的空实现。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)   
 [IRowsetNotifyCP 类](../../data/oledb/irowsetnotifycp-class.md)