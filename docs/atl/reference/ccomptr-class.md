---
title: CComPtr 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
dev_langs:
- C++
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bba9e3cce5424fdba86c05c0fd94cb3a0d08a5bb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030919"
---
# <a name="ccomptr-class"></a>CComPtr 类

用于管理 COM 接口指针的智能指针类。

## <a name="syntax"></a>语法

```
template<class T>
class CComPtr
```

#### <a name="parameters"></a>参数

*T*<br/>
指定要存储的指针的类型的 COM 接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CComPtr::operator =](#operator_eq)|将一个指针分配给成员指针。|

## <a name="remarks"></a>备注

使用 ATL`CComPtr`并[CComQIPtr](../../atl/reference/ccomqiptr-class.md)来管理 COM 接口指针。 派生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)，并同时执行自动引用计数。

`CComPtr`并[CComQIPtr](../../atl/reference/ccomqiptr-class.md)类可帮助避免内存泄漏，通过执行自动引用计数。  以下函数这两个执行相同的逻辑操作;但是，请注意如何第二个版本可能是更不易于出错使用`CComPtr`类：

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

在调试版本链接代码跟踪的 atlsd.lib。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="ccomptr"></a>  CComPtr::CComPtr

构造函数。

```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>参数

*lp*<br/>
用于初始化的接口指针。

*T*<br/>
COM 接口。

##  <a name="operator_eq"></a>  CComPtr::operator =

赋值运算符。

```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>返回值

返回一个指向已更新`CComPtr`对象

### <a name="remarks"></a>备注

现有对象，如果存在此操作 AddRefs 新对象和版本。

## <a name="see-also"></a>请参阅

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[类概述](../../atl/atl-class-overview.md)
