---
title: CComPtr 类
description: Microsoft C++活动模板库 （ATL） 类 CComPtr 的参考指南。
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 855466225db2672755658dcbbc9a266d09e0e7be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327525"
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
指定要存储的指针类型的 COM 接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComPtr：CComPtr](#ccomptr)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CComPtr：：运算符 |](#operator_eq)|分配指向成员指针的指针。|

## <a name="remarks"></a>备注

ATL`CComPtr`使用[CComQIPtr](../../atl/reference/ccomqiptr-class.md)来管理 COM 接口指针。 两者都来自[CComPtrBase，](../../atl/reference/ccomptrbase-class.md)并且都执行自动引用计数。

`CComPtr`和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)类可以通过执行自动引用计数来帮助消除内存泄漏。  以下函数都执行相同的逻辑操作。 但是，第二个版本可能不太容易出错，因为它使用类`CComPtr`：

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

在调试版本中，链接 atlsd.lib 进行代码跟踪。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomptrccomptr"></a><a name="ccomptr"></a>CComPtr：CComPtr

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

在`AddRef`*lp*上获取参数调用的构造函数，如果它不是空指针。 非空拥有的对象获取对 CComPtr 对象的破坏的`Release`调用，或者如果将新对象分配给 CComPtr 对象。

## <a name="ccomptroperator-"></a><a name="operator_eq"></a>CComPtr：：运算符 |

赋值运算符。

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>返回值

返回指向更新`CComPtr`对象的指针

### <a name="remarks"></a>备注

此操作 AddRef 新对象并释放现有对象（如果存在）。

## <a name="see-also"></a>另请参阅

[CComPtr：CComPtr](#ccomptr)<br/>
[CComQIPtr：CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[类概述](../../atl/atl-class-overview.md)
