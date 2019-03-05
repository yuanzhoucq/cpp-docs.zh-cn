---
title: CAtlException 类
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: a6ed6062be02fddc111e4eda4d26226b7a7a0c63
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296080"
---
# <a name="catlexception-class"></a>CAtlException 类

此类定义 ATL 异常。

## <a name="syntax"></a>语法

```
class CAtlException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAtlException::operator HRESULT](#operator_hresult)|将强制转换为 HRESULT 值的当前对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAtlException::m_hr](#m_hr)|创建的对象的 HRESULT 以及用来存储错误条件的类型的变量。|

## <a name="remarks"></a>备注

一个`CAtlException`对象都表示对 ATL 操作相关的异常条件。 `CAtlException`类包括存储，该值指示该异常并使您可以将该异常，就好像 HRESULT 的强制转换运算符的原因的状态代码的公共数据成员。

一般情况下，将调用`AtlThrow`而不是创建`CAtlException`直接对象。

## <a name="requirements"></a>要求

**标头：** atlexcept.h

##  <a name="catlexception"></a>  CAtlException::CAtlException

构造函数。

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>参数

*hr*<br/>
HRESULT 错误代码。

##  <a name="operator_hresult"></a>  CAtlException::operator HRESULT

将强制转换为 HRESULT 值的当前对象。

```
operator HRESULT() const throw ();
```

##  <a name="m_hr"></a>  CAtlException::m_hr

HRESULT 数据成员。

```
HRESULT m_hr;
```

### <a name="remarks"></a>备注

将存储的错误条件的数据成员。 HRESULT 值由构造函数中，设置[CAtlException::CAtlException](#catlexception)。

## <a name="see-also"></a>请参阅

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[类概述](../../atl/atl-class-overview.md)
