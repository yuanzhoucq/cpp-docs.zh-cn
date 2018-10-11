---
title: CEnumerator 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6f85fafe213fa7e53f67fb6a3035f415235c8794
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082444"
---
# <a name="cenumerator-class"></a>CEnumerator 类

使用公开的 OLE DB 枚举器对象[ISourcesRowset](/previous-versions/windows/desktop/ms715969)接口以返回行集描述所有数据源和枚举器。  
  
## <a name="syntax"></a>语法

```cpp
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  

## <a name="requirements"></a>要求  

**标头：** atldbcli.h
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[查找](#find)|搜索可用的提供程序（数据源），查找一个具有指定名称的提供程序。|  
|[GetMoniker](#getmoniker)|检索当前记录的 `IMoniker` 接口。|  
|[打开](#open)|打开枚举器。|  
  
## <a name="remarks"></a>备注  

可以检索`ISourcesRowset`从此类间接的数据。  

## <a name="find"></a> Cenumerator:: Find

在可用提供程序之间查找指定名称。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>参数  

*szSearchName*<br/>
[in] 要搜索的名称。  
  
### <a name="return-value"></a>返回值  

**true**如果已找到的名称。 否则为**false**。  
  
### <a name="remarks"></a>备注  

此名称将映射到`SOURCES_NAME`的成员[ISourcesRowset](/previous-versions/windows/desktop/ms715969)接口。  
  
## <a name="getmoniker"></a> Cenumerator:: Getmoniker

分析要提取的字符串可以转换为一个名字对象的组件的显示名称。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();  

HRESULT GetMoniker(LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*ppMoniker*<br/>
[out]显示名称从分析的名字对象 ([cenumeratoraccessor:: M_szparsename](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) 的当前行。  
  
*lpszDisplayName*<br/>
[in]要分析的显示名称。  
  
### <a name="return-value"></a>返回值  

标准的 HRESULT。  

## <a name="open"></a> Cenumerator:: Open

将名字对象绑定枚举器，如果其中一个指定，则检索行集枚举器通过调用[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200)。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT Open(LPMONIKER pMoniker) throw();  

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();  

HRESULT Open(const CEnumerator& enumerator) throw();  
```  
  
#### <a name="parameters"></a>参数  

*pMoniker*<br/>
[in]指向一个枚举器的名字对象的指针。  
  
*pClsid*<br/>
[in]一个指向`CLSID`的一个枚举器。  
  
*enumerator*<br/>
[in]对枚举器的引用。  
  
### <a name="return-value"></a>返回值  

标准的 HRESULT。  
  
## <a name="see-also"></a>请参阅  

[DBViewer](../../visual-cpp-samples.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)