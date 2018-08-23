---
title: CRestrictions 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b9dc35df928d53d7d5ca5d833db8e87c96e1c7f4
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572544"
---
# <a name="crestrictions-class"></a>CRestrictions 类
泛型类，可用于指定架构行集的限制。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, short nRestrictions, const GUID* pguid>  
class CRestrictions : 
   public CSchemaRowset <T, nRestrictions>  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 取值函数使用的类。  
  
 *nRestrictions*  
 架构行集的限制列数。  
  
 *pguid*  
 指向架构的 GUID 的指针。  

## <a name="requirements"></a>要求  
 **标头：** atldbsch.h 
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[打开](#open)|返回一个结果集，根据用户提供的限制。|   

## <a name="open"></a> Crestrictions:: Open
返回一个结果集，根据用户提供的限制。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true);  
```  
  
#### <a name="parameters"></a>参数  
 *会话*  
 [in]指定用于连接到数据源的现有会话对象。  
  
 *lpszParam*  
 [in]架构行集上指定的限制。  
  
 *bBind*  
 [in]指定是否自动绑定列映射。 默认值是 **，则返回 true**，这将导致自动绑定的列映射。 设置*bBind*到**false**可防止自动绑定列映射，以便您可以手动绑定。 （手动绑定是 OLAP 用户特别关注。）  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 架构行集上，可以指定最多七个限制。  
  
 请参阅[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))有关每个架构行集上定义的限制信息。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)    
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)