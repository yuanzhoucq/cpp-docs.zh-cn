---
title: CAccessorBase 类
ms.date: 11/04/2016
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
ms.openlocfilehash: e29883b2a42010daee19f915c49c31686b232cf6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233452"
---
# <a name="caccessorbase-class"></a>CAccessorBase 类

OLE DB 模板中的所有访问器都从此类派生。 `CAccessorBase`允许一个行集管理多个访问器。 它还提供了参数和输出列的绑定。

## <a name="syntax"></a>语法

```cpp
// Replace with syntax
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[关闭](#close)|关闭访问器。|
|[GetHAccessor](#geth)|检索访问器句柄。|
|[GetNumAccessors](#getnum)|检索类创建的取值函数数目。|
|[IsAutoAccessor](#isauto)|测试指定的访问器是否为 autoaccessor。|
|[ReleaseAccessors](#release)|释放访问器。|

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="caccessorbaseclose"></a><a name="close"></a>CAccessorBase：： Close

关闭访问器。

### <a name="syntax"></a>语法

```cpp
void Close();
```

### <a name="remarks"></a>备注

必须先调用[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md) 。

## <a name="caccessorbasegethaccessor"></a><a name="geth"></a>CAccessorBase：： GetHAccessor

检索指定访问器的访问器句柄。

### <a name="syntax"></a>语法

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>参数

*nAccessor*<br/>
[in] 访问器的零偏移量。

### <a name="return-value"></a>返回值

访问器句柄。

## <a name="caccessorbasegetnumaccessors"></a><a name="getnum"></a>CAccessorBase：： GetNumAccessors

检索类创建的取值函数数目。

### <a name="syntax"></a>语法

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>返回值

类创建的取值函数数目。

## <a name="caccessorbaseisautoaccessor"></a><a name="isauto"></a>CAccessorBase：： IsAutoAccessor

如果在移动操作过程中自动为访问器检索数据，则返回 true。

### <a name="syntax"></a>语法

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>参数

*nAccessor*<br/>
[in] 访问器的零偏移量。

### <a name="return-value"></a>返回值

**`true`** 如果访问器是 autoaccessor，则返回。 否则，它将返回 **`false`** 。

## <a name="caccessorbasereleaseaccessors"></a><a name="release"></a>CAccessorBase：： ReleaseAccessors

释放由类创建的访问器。

### <a name="syntax"></a>语法

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>参数

*pUnk*<br/>
中指向为 `IUnknown` 其创建了访问器的 COM 对象的接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

从[CAccessorRowset：： Close](../../data/oledb/caccessorrowset-close.md)调用。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase 类](../../data/oledb/caccessorbase-class.md)
