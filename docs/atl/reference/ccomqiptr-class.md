---
title: CComQIPtr 类
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: 64716d945ffbc6802ec23fb47523464246065192
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298810"
---
# <a name="ccomqiptr-class"></a>CComQIPtr 类

用于管理 COM 接口指针的智能指针类。

## <a name="syntax"></a>语法

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
指定要存储的指针的类型的 COM 接口。

*piid*<br/>
指向 IID *T*。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CComQIPtr::operator =](#operator_eq)|将一个指针分配给成员指针。|

## <a name="remarks"></a>备注

使用 ATL`CComQIPtr`并[CComPtr](../../atl/reference/ccomptr-class.md)若要管理 COM 接口指针，这两个派生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)。 这两个类执行自动引用计数通过调用`AddRef`和`Release`。 重载的运算符处理指针操作。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>要求

**标头：** atlcomcli.h

##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr

构造函数。

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>参数

*lp*<br/>
用于初始化的接口指针。

*T*<br/>
COM 接口。

*piid*<br/>
指向 IID *T*。

##  <a name="operator_eq"></a>  CComQIPtr::operator =

赋值运算符。

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>参数

*lp*<br/>
用于初始化的接口指针。

*T*<br/>
COM 接口。

*piid*<br/>
指向 IID *T*。

### <a name="return-value"></a>返回值

返回一个指向已更新`CComQIPtr`对象。

## <a name="see-also"></a>请参阅

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase 类](../../atl/reference/ccomptrbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)
