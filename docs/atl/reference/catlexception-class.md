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
ms.openlocfilehash: 6da56e4d6c443520eb6f857624a5923e71a1e580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318997"
---
# <a name="catlexception-class"></a>CAtlException 类

此类定义 ATL 异常。

## <a name="syntax"></a>语法

```
class CAtlException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[例外：CAtlException](#catlexception)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAtlException：：操作员 HRESULT](#operator_hresult)|将当前对象强制转换为 HRESULT 值。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAtlException：m_hr](#m_hr)|由对象创建并用于存储错误条件的 HRESULT 类型的变量。|

## <a name="remarks"></a>备注

`CAtlException`对象表示与 ATL 操作相关的异常条件。 类`CAtlException`包括存储指示异常原因的状态代码的公共数据成员，以及允许您将异常视为 HRESULT 的强制转换运算符。

通常，您将调用`AtlThrow`而不是直接创建`CAtlException`对象。

## <a name="requirements"></a>要求

**标题：** atlexcept.h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>例外：CAtlException

构造函数。

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>参数

*人力资源*<br/>
HRESULT 错误代码。

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException：：操作员 HRESULT

将当前对象强制转换为 HRESULT 值。

```
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException：m_hr

HRESULT 数据成员。

```
HRESULT m_hr;
```

### <a name="remarks"></a>备注

存储错误条件的数据成员。 HRESULT 值由构造函数[CAtlException 设置：：CAtlexception](#catlexception)。

## <a name="see-also"></a>另请参阅

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[类概述](../../atl/atl-class-overview.md)
