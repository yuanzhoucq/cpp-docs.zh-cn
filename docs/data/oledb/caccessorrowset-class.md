---
title: "CAccessorRowset 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
dev_langs: C++
helpviewer_keywords: CAccessorRowset class
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9750393a96a504b20ce861624ba94f8336fd9d4f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="caccessorrowset-class"></a>CAccessorRowset 类
封装一个行集和单个类中其关联的访问器。  
  
## <a name="syntax"></a>语法  
  
```  
template <   
   class TAccessor = CNoAccessor,    
   template <typename T> class TRowset = CRowset    
>  
class CAccessorRowset :   
   public TAccessor,    
   public TRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>参数  
 `TAccessor`  
 一个访问器类。  
  
 `TRowset`  
 行集类。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[绑定](../../data/oledb/caccessorrowset-bind.md)|创建绑定 (时使用**bBind**指定为 false 在[ccommand:: Open](../../data/oledb/ccommand-open.md))。|  
|[CAccessorRowset](../../data/oledb/caccessorrowset-caccessorrowset.md)|构造函数。|  
|[关闭](../../data/oledb/caccessorrowset-close.md)|关闭具有行集和任何访问器。|  
|[FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md)|释放当前需要被释放的记录中的任何列。|  
|[GetColumnInfo](../../data/oledb/caccessorrowset-getcolumninfo.md)|实现[IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)。|  
  
## <a name="remarks"></a>备注  
 类`TAccessor`管理访问器。 类*TRowset*管理行集。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)