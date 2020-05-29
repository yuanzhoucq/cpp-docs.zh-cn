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
ms.openlocfilehash: f09d9b2f46233cf356f5ade8a5b90e08a213d276
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168197"
---
# <a name="catlexception-class"></a>CAtlException 类

此类定义 ATL 异常。

## <a name="syntax"></a>语法

```cpp
class CAtlException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAtlException：： operator HRESULT](#operator_hresult)|将当前对象强制转换为 HRESULT 值。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAtlException：： m_hr](#m_hr)|类型为 HRESULT 的变量，该对象由对象创建并用于存储错误条件。|

## <a name="remarks"></a>备注

`CAtlException`对象表示与 ATL 操作相关的异常条件。 `CAtlException`类包含一个公共数据成员，该成员存储指示异常原因的状态代码，并使用一个转换运算符来将异常视为 HRESULT。

通常，您将调用`AtlThrow` ，而不是直接`CAtlException`创建对象。

## <a name="requirements"></a>要求

**标头：** atlexcept

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

构造函数。

```cpp
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>参数

*人事*<br/>
HRESULT 错误代码。

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException：： operator HRESULT

将当前对象强制转换为 HRESULT 值。

```cpp
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException：： m_hr

HRESULT 数据成员。

```cpp
HRESULT m_hr;
```

### <a name="remarks"></a>备注

存储错误条件的数据成员。 HRESULT 值是由构造函数[CAtlException：： CAtlException](#catlexception)设置的。

## <a name="see-also"></a>另请参阅

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[类概述](../../atl/atl-class-overview.md)
