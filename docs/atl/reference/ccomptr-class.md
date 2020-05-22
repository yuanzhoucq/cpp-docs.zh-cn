---
title: CComPtr 类
description: Microsoft C++活动模板库（ATL）类 CComPtr 的参考指南。
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 74a12b460f55a782fa2747b02f7d00287786fae6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127400"
---
# <a name="ccomptr-class"></a>CComPtr 类

用于管理 COM 接口指针的智能指针类。

## <a name="syntax"></a>语法

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>参数

*T*<br/>
一个 COM 接口，指定要存储的指针的类型。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComPtr：： CComPtr](#ccomptr)|构造函数。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[CComPtr：： operator =](#operator_eq)|分配指向成员指针的指针。|

## <a name="remarks"></a>备注

ATL 使用 `CComPtr` 和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)管理 COM 接口指针。 两者均派生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)，它们都执行自动引用计数。

`CComPtr` 和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)类可以通过执行自动引用计数来帮助消除内存泄露。  以下函数执行相同的逻辑操作。 但是，第二个版本可能不容易出错，因为它使用 `CComPtr` 类：

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

在调试版本中，将 atlsd.lib 链接到代码跟踪。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>要求

**标头：** atlbase.h

## <a name="ccomptr"></a>CComPtr：： CComPtr

构造函数。

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>参数

*lp*<br/>
用于初始化接口指针。

*T*<br/>
COM 接口。

### <a name="remarks"></a>备注

采用自变量调用的构造函数如果不是 null 指针，则 `AddRef` *lp*。 非 null 拥有的对象将获取 CComPtr 对象的析构上的 `Release` 调用，或如果将新对象分配给 CComPtr 对象，则为。

## <a name="operator_eq"></a>CComPtr：： operator =

赋值运算符。

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>返回值

返回指向已更新 `CComPtr` 对象的指针

### <a name="remarks"></a>备注

此操作 AddRefs 新的对象并释放现有对象（如果存在）。

## <a name="see-also"></a>另请参阅

[CComPtr：： CComPtr](#ccomptr)<br/>
[CComQIPtr：： CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[类概述](../../atl/atl-class-overview.md)
