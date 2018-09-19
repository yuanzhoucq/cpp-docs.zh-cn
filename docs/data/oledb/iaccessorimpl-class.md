---
title: IAccessorImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
dev_langs:
- C++
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0fd40d4cac87302a6a636693e0da4480720a2cf3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098109"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl 类

提供的实现[IAccessor](/previous-versions/windows/desktop/ms719672\(v=vs.85\))接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, 
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
### <a name="parameters"></a>参数  

*T*<br/>
行集或命令对象类。  
  
*BindType*<br/>
绑定信息的存储单位。 默认值是`ATLBINDINGS`结构 （请参阅 atldb.h）。  
  
*BindingVector*<br/>
列信息的存储单元。 默认值是[CAtlMap](../../atl/reference/catlmap-class.md)其中的关键元素是 HACCESSOR 值，值元素是一个指向`BindType`结构。  
  
## <a name="requirements"></a>要求  

**标头：** atldb.h  

## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[IAccessorImpl](#iaccessorimpl)|构造函数。|  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[AddRefAccessor](#addrefaccessor)|将引用计数添加到现有的访问器。|  
|[CreateAccessor](#createaccessor)|从一组绑定创建取值函数。|  
|[GetBindings](#getbindings)|访问器中返回的绑定。|  
|[ReleaseAccessor](#releaseaccessor)|释放访问器。|  
  
## <a name="remarks"></a>备注  

这是必需的对于行集和命令。 OLE DB 要求提供商实现 HACCESSOR，这是一种标记的数组[DBBINDING](/previous-versions/windows/desktop/ms716845\(v=vs.85\))结构。 提供的 HACCESSORs`IAccessorImpl`是地址`BindType`结构。 默认情况下`BindType`指`ATLBINDINGS`中`IAccessorImpl`的模板定义。 `BindType` 提供使用的一种机制`IAccessorImpl`跟踪中的元素数及其`DBBINDING`数组以及引用计数和访问器标志。  

## <a name="iaccessorimpl"></a> Iaccessorimpl:: Iaccessorimpl

构造函数。  
  
### <a name="syntax"></a>语法  
  
```cpp
IAccessorImpl();  
```  

## <a name="addrefaccessor"></a> Iaccessorimpl:: Addrefaccessor

将引用计数添加到现有的访问器。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[IAccessor::AddRefAccessor](/previous-versions/windows/desktop/ms714978\(v=vs.85\))中*OLE DB 程序员参考*。

## <a name="createaccessor"></a> Iaccessorimpl:: Createaccessor

从一组绑定创建取值函数。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,  
   DBCOUNTITEM cBindings,  
   const DBBINDING rgBindings[],  
   DBLENGTH cbRowSize,  
   HACCESSOR* phAccessor,  
   DBBINDSTATUS rgStatus[]);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[iaccessor:: Createaccessor](/previous-versions/windows/desktop/ms720969\(v=vs.85\))中*OLE DB 程序员参考*。  

## <a name="getbindings"></a> Iaccessorimpl:: Getbindings

从访问器中的使用者返回的基本列绑定。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,  
   DBACCESSORFLAGS* pdwAccessorFlags,  
   DBCOUNTITEM* pcBindings,  
   DBBINDING** prgBindings);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[IAccessor::GetBindings](/previous-versions/windows/desktop/ms721253\(v=vs.85\))中*OLE DB 程序员参考*。 

## <a name="releaseaccessor"></a> Iaccessorimpl:: Releaseaccessor

释放访问器。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[iaccessor:: Releaseaccessor](/previous-versions/windows/desktop/ms719717\(v=vs.85\))中*OLE DB 程序员参考*。
  
## <a name="see-also"></a>请参阅  

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)