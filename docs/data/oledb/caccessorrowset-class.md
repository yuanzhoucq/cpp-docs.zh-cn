---
title: CAccessorRowset 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- FreeRecordMemory
- GetColumnInfo
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 85f08ae7a996a762be915bcce820c33a0a8e549c
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572130"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset 类
封装一个行集和其关联的访问器的单个类。  
  
## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CNoAccessor, 
   template <typename T> class TRowset = CRowset>  
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>  
```  
  
### <a name="parameters"></a>参数  
 *TAccessor*  
 一个访问器类。  
  
 *TRowset*  
 行集类。  

## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[将绑定](#bind)|创建绑定 (使用何时`bBind`指定为**false**中[ccommand:: Open](../../data/oledb/ccommand-open.md))。|  
|[CAccessorRowset](#caccessorrowset)|构造函数。|  
|[关闭](#close)|关闭的行集和任何访问器。|  
|[FreeRecordMemory](#freerecordmemory)|释放当前需要释放的记录中的任何列。|  
|[GetColumnInfo](#getcolumninfo)|实现[icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))。|  
  
## <a name="remarks"></a>备注  
 类`TAccessor`管理访问器。 类*TRowset*管理行集。  

## <a name="bind"></a> Caccessorrowset:: Bind
如果你指定创建绑定`bBind`作为**false**中[ccommand:: Open](../../data/oledb/ccommand-open.md)。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT Bind();  
```  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。  

## <a name="caccessorrowset"></a> Caccessorrowset:: Caccessorrowset
初始化 `CAccessorRowset` 对象。  
  
### <a name="syntax"></a>语法  
  
```cpp
CAccessorRowset();  
```  

## <a name="close"></a> Caccessorrowset:: Close
释放任何活动的访问器和行集。  
  
### <a name="syntax"></a>语法  
  
```cpp
void Close();  
```  
  
### <a name="remarks"></a>备注  
 释放关联的任何内存。  

## <a name="freerecordmemory"></a> Caccessorrowset:: Freerecordmemory
释放当前需要释放的记录中的任何列。  
  
### <a name="syntax"></a>语法  
  
```cpp
void FreeRecordMemory();  
```  

## <a name="getcolumninfo"></a> Caccessorrowset:: Getcolumninfo
从打开的行集中获取列信息。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns, 
   DBCOLUMNINFO** ppColumnInfo, 
   LPOLESTR* ppStrings) const; 
    
HRESULT GetColumnInfo(DBORDINAL* pColumns, 
   DBCOLUMNINFO** ppColumnInfo);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中*OLE DB 程序员参考*。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。  
  
### <a name="remarks"></a>备注  
 用户必须释放返回的列信息和字符串缓冲区。 当你使用时使用此方法的第二个版本[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)和需要重写这些绑定。  
  
 有关详细信息，请参阅[icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中*OLE DB 程序员参考*。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)