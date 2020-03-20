---
title: IAccessorImpl 类
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
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
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: f1865089100ac7f60e8c011e72eedb3d0a3f8470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545989"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl 类

提供[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>parameters

*T*<br/>
行集或命令对象类。

*BindType*<br/>
绑定信息的存储单元。 默认值是 `ATLBINDINGS` 结构（请参阅为 atldb.h）。

*BindingVector*<br/>
列信息的存储单位。 默认值为[CAtlMap](../../atl/reference/catlmap-class.md) ，其中 key 元素是 HACCESSOR 值，值元素是指向 `BindType` 结构的指针。

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
|[AddRefAccessor](#addrefaccessor)|向现有的访问器添加引用数。|
|[CreateAccessor](#createaccessor)|从一组绑定创建访问器。|
|[GetBindings](#getbindings)|返回访问器中的绑定。|
|[ReleaseAccessor](#releaseaccessor)|释放访问器。|

## <a name="remarks"></a>备注

这对于行集和命令是必需的。 OLE DB 要求提供程序实现 HACCESSOR，它是[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))结构数组的标记。 `IAccessorImpl` 提供的 HACCESSORs 是 `BindType` 结构的地址。 默认情况下，`BindType` 在 `IAccessorImpl`模板定义中定义为 `ATLBINDINGS`。 `BindType` 提供了一种机制，`IAccessorImpl` 用于跟踪其 `DBBINDING` 数组中的元素数，以及引用计数和访问器标志。

## <a name="iaccessorimpliaccessorimpl"></a><a name="iaccessorimpl"></a>IAccessorImpl：： IAccessorImpl

构造函数。

### <a name="syntax"></a>语法

```cpp
IAccessorImpl();
```

## <a name="iaccessorimpladdrefaccessor"></a><a name="addrefaccessor"></a>IAccessorImpl：： AddRefAccessor

向现有的访问器添加引用数。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IAccessor：： AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) 。

## <a name="iaccessorimplcreateaccessor"></a><a name="createaccessor"></a>IAccessorImpl：： CreateAccessor

从一组绑定创建访问器。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IAccessor：： CreateAccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) 。

## <a name="iaccessorimplgetbindings"></a><a name="getbindings"></a>IAccessorImpl：： GetBindings

返回访问器中来自使用者的基本列绑定。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IAccessor：： GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) 。

## <a name="iaccessorimplreleaseaccessor"></a><a name="releaseaccessor"></a>IAccessorImpl：： ReleaseAccessor

释放访问器。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IAccessor：： ReleaseAccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) 。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)