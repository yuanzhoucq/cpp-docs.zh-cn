---
title: CAccessorBase 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2e62c4242513c5147dcfd84ee5d69ec51a4816d1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053326"
---
# <a name="caccessorbase-class"></a>CAccessorBase 类

OLE DB 模板中的所有访问器从此类派生。 `CAccessorBase` 允许一个行集来管理多个访问器。 它还提供有关参数和输出列的绑定。

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
|[GetNumAccessors](#getnum)|检索类创建的取值函数的数目。|
|[IsAutoAccessor](#isauto)|测试指定的取值函数是否为自动访问器。|
|[ReleaseAccessors](#release)|释放访问器。|

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="close"></a> Caccessorbase:: Close

关闭访问器。

### <a name="syntax"></a>语法

```cpp
void Close();
```

### <a name="remarks"></a>备注

必须调用[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md)第一个。

## <a name="geth"></a> Caccessorbase:: Gethaccessor

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

## <a name="getnum"></a> Caccessorbase:: Getnumaccessors

检索类创建的取值函数的数目。

### <a name="syntax"></a>语法

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>返回值

访问器类创建的数。

## <a name="isauto"></a> Caccessorbase:: Isautoaccessor

如果自动检索数据的访问器在移动操作期间，则返回 true。

### <a name="syntax"></a>语法

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>参数

*nAccessor*<br/>
[in] 访问器的零偏移量。

### <a name="return-value"></a>返回值

返回 **，则返回 true**如果访问器为自动访问器。 否则，返回 **false**。

## <a name="release"></a> Caccessorbase:: Releaseaccessors

释放访问器类创建的。

### <a name="syntax"></a>语法

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>参数

*pUnk*<br/>
[in]一个指向`IUnknown`为其创建访问器的 COM 对象的接口。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

从调用[caccessorrowset:: Close](../../data/oledb/caccessorrowset-close.md)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase 类](../../data/oledb/caccessorbase-class.md)