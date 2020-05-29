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
ms.openlocfilehash: 2b1d8b92fbc5e95a5061956bafc4922d249a6f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327422"
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
指定要存储的指针类型的 COM 接口。

*皮伊德*<br/>
指向*T*的 IID 的指针。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComQIPtr：CComQIPtr](#ccomqiptr)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CComQIPtr：：操作员 |](#operator_eq)|分配指向成员指针的指针。|

## <a name="remarks"></a>备注

ATL`CComQIPtr`使用和[CComPtr](../../atl/reference/ccomptr-class.md)来管理 COM 接口指针，这两个指针都派生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)。 两个类都通过调用`AddRef`和`Release`执行自动引用计数。 重载运算符处理指针操作。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>要求

**标题：** atlcomcli.h

## <a name="ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a>CComQIPtr：CComQIPtr

构造函数。

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>参数

*lp*<br/>
用于初始化接口指针。

*T*<br/>
COM 接口。

*皮伊德*<br/>
指向*T*的 IID 的指针。

## <a name="ccomqiptroperator-"></a><a name="operator_eq"></a>CComQIPtr：：操作员 |

分配运算符。

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>参数

*lp*<br/>
用于初始化接口指针。

*T*<br/>
COM 接口。

*皮伊德*<br/>
指向*T*的 IID 的指针。

### <a name="return-value"></a>返回值

返回指向更新`CComQIPtr`对象的指针。

## <a name="see-also"></a>另请参阅

[CComPtr：CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr：CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase 类](../../atl/reference/ccomptrbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)
