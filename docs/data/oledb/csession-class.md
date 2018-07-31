---
title: CSession 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
dev_langs:
- C++
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 72ac1a5be4f2e114e5b90b65542b09733c43d174
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338858"
---
# <a name="csession-class"></a>CSession 类
表示单个数据库访问会话。  
  
## <a name="syntax"></a>语法

```cpp
class CSession  
```  

## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[中止](#abort)|取消（终止）事务。|  
|[关闭](#close)|关闭会话。|  
|[提交](#commit)|提交事务。|  
|[GetTransactionInfo](#gettransactioninfo)|返回有关事务的信息。|  
|[打开](#open)|为数据源对象打开新会话。|  
|[StartTransaction](#starttransaction)|开始此会话的新事务。|  
  
## <a name="remarks"></a>备注  
 一个或多个会话可以与每个提供程序连接 （数据源），由表示相关联[CDataSource](../../data/oledb/cdatasource-class.md)对象。 若要创建一个新`CSession`有关`CDataSource`，调用[csession:: Open](../../data/oledb/csession-open.md)。 为了开始数据库事务，`CSession` 提供了 `StartTransaction` 方法。 事务启动后，您可以提交使用与其`Commit`方法，或取消它使用`Abort`方法。  
  
## <a name="abort"></a> Csession:: Abort
将终止该事务。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT Abort(BOID* pboidReason = NULL,   
   BOOL bRetaining = FALSE,   
   BOOL bAsync = FALSE) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[itransaction:: Abort](https://msdn.microsoft.com/library/ms709833.aspx)中*OLE DB 程序员参考*。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。 

## <a name="close"></a> Csession:: Close
关闭该会话，打开[csession:: Open](../../data/oledb/csession-open.md)。  
  
### <a name="syntax"></a>语法  
  
```cpp
void Close() throw();  
```  
  
### <a name="remarks"></a>备注  
 版本`m_spOpenRowset`指针。  

## <a name="commit"></a> Csession:: Commit
提交事务。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT Commit(BOOL bRetaining = FALSE,   
   DWORD grfTC = XACTTC_SYNC,   
   DWORD grfRM = 0) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[itransaction:: Commit](https://msdn.microsoft.com/library/ms713008.aspx)中*OLE DB 程序员参考*。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[itransaction:: Commit](https://msdn.microsoft.com/library/ms713008.aspx)。  

## <a name="gettransactioninfo"></a> Csession:: Gettransactioninfo
返回有关事务的信息。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ITransaction::GetTransactionInfo](https://msdn.microsoft.com/library/ms714975.aspx)中*OLE DB 程序员参考*。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[ITransaction::GetTransactionInfo](https://msdn.microsoft.com/library/ms714975.aspx)中*OLE DB 程序员参考*。 

## <a name="open"></a> Csession:: Open
为数据源对象打开新会话。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT Open(const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *ds*  
 [in]该会话将打开数据源。  
  
 *pPropSet*  
 [in]指向数组的指针[DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx)结构包含要设置属性和值。 请参阅[属性设置和属性组](https://msdn.microsoft.com/library/ms713696.aspx)中*OLE DB 程序员参考*Windows SDK 中。  
  
 *ulPropSets*  
 [in]数[DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx)结构传入*pPropSet*参数。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。  
  
### <a name="remarks"></a>备注  
 必须打开数据源对象使用[cdatasource:: Open](../../data/oledb/cdatasource-open.md)之前将其传递给`CSession::Open`。  

## <a name="starttransaction"></a> Csession:: Starttransaction
开始此会话的新事务。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,  
   ULONG isoFlags = 0,  
   ITransactionOptions* pOtherOptions = NULL,  
   ULONG* pulTransactionLevel = NULL) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[itransactionlocal:: Starttransaction](https://msdn.microsoft.com/library/ms709786.aspx)中*OLE DB 程序员参考*。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[itransactionlocal:: Starttransaction](https://msdn.microsoft.com/library/ms709786.aspx)中*OLE DB 程序员参考*。 
  
## <a name="see-also"></a>请参阅  
 [CatDB](../../visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)