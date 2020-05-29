---
title: ComPtrRef 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
- client/Microsoft::WRL::Details::ComPtrRef::operator==
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
- client/Microsoft::WRL::Details::ComPtrRef::operator*
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRef class
- Microsoft::WRL::Details::ComPtrRef::ComPtrRef, constructor
- Microsoft::WRL::Details::ComPtrRef::GetAddressOf method
- Microsoft::WRL::Details::ComPtrRef::operator== operator
- Microsoft::WRL::Details::ComPtrRef::operator!= operator
- Microsoft::WRL::Details::ComPtrRef::operator InterfaceType** operator
- Microsoft::WRL::Details::ComPtrRef::operator* operator
- Microsoft::WRL::Details::ComPtrRef::operator T* operator
- Microsoft::WRL::Details::ComPtrRef::operator void** operator
- Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf method
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
ms.openlocfilehash: df9ded817227547493c04035e0abc3d948e24495
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372624"
---
# <a name="comptrref-class"></a>ComPtrRef 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>参数

*T*<br/>
[ComPtr\<T>](comptr-class.md)类型或从它派生的类型，而不仅仅是 由 表示的`ComPtr`接口。

## <a name="remarks"></a>备注

表示对类型`ComPtr<T>`对象的引用。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                               | 说明
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef：ComPtrRef](#comptrref) | 从指定的指针初始化`ComPtrRef`类的新实例到另一个`ComPtrRef`对象。

### <a name="public-methods"></a>公共方法

名称                                                         | 说明
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef：获取地址](#getaddressof)                     | 检索指向当前`ComPtrRef`对象表示的接口的指针的地址。
[Comptrref：：发布和获取地址](#releaseandgetaddressof) | 删除当前`ComPtrRef`对象，并返回指向对象表示的接口的`ComPtrRef`指针指向指针。

### <a name="public-operators"></a>公共运算符

名称                                                                     | 说明
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef：：操作员接口类型*](#operator-interfacetype-star-star) | 删除当前`ComPtrRef`对象，并返回指向对象表示的接口的`ComPtrRef`指针指向指针。
[ComPtrRef：：运算符 T*](#operator-t-star)                               | 返回当前 ComPtrRef 对象的[ptr_](comptrrefbase-class.md#ptr)数据成员的值。
[ComPtrRef：：操作员空隙*](#operator-void-star-star)                   | 删除当前`ComPtrRef`对象，将指向`ComPtrRef`该对象表示的接口的指针转换为指针到`void`指针到 ，然后返回强制转换指针。
[ComPtrRef：操作员*](#operator-star)                                   | 检索指向当前`ComPtrRef`对象表示的接口的指针。
[ComPtrRef：：运算符 *](#operator-equality)                              | 指示两个 `ComPtrRef` 对象是否相等。
[ComPtrRef：操作员！](#operator-inequality)                            | 指示两个 `ComPtrRef` 对象是否不相等。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** 微软：：WRL：:D

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>ComPtrRef：ComPtrRef

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>参数

*Ptr*<br/>
另一个`ComPtrRef`对象的基础值。

### <a name="remarks"></a>备注

从指定的指针初始化`ComPtrRef`类的新实例到另一个`ComPtrRef`对象。

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef：获取地址

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>返回值

指向当前`ComPtrRef`对象表示的接口的指针的地址。

### <a name="remarks"></a>备注

检索指向当前`ComPtrRef`对象表示的接口的指针的地址。

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef：：运算符 *

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>参数

*a*<br/>
对 `ComPtrRef` 对象的引用。

*B*<br/>
对另一个`ComPtrRef`对象的引用，或指向匿名类型的指针 （`void*`。

### <a name="return-value"></a>返回值

如果对象*a*等于对象*b，* 则第一个运算符将生成**为 true。** 否则，**假**。

**如果对象** *a*等于**nullptr，** 则第二个和第三个运算符将 true。否则，**假**。

**如果对象**a 等于对象*b，* 则第四和第*b*五运算符将 true;否则，**假**。

### <a name="remarks"></a>备注

指示两个 `ComPtrRef` 对象是否相等。

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef：操作员！

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>参数

*a*<br/>
对 `ComPtrRef` 对象的引用。

*B*<br/>
对另`ComPtrRef`一个对象的引用，或指向匿名对象的指针 （`void*`。

### <a name="return-value"></a>返回值

如果对象 a 不等于对象*b，* 则第*b*一个运算符将生成**为 true。** 否则，**假**。

**如果对象** *a*不等于**nullptr，** 则第二个和第三个运算符将 true。否则，**假**。

**如果对象**a 不等于对象*b，* 则第四和第*b*五运算符将 true。否则，**假**。

### <a name="remarks"></a>备注

指示两个 `ComPtrRef` 对象是否不相等。

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef：：操作员接口类型*

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>备注

删除当前`ComPtrRef`对象，并返回指向对象表示的接口的`ComPtrRef`指针指向指针。

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef：操作员*

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>返回值

指向当前`ComPtrRef`对象表示的接口的指针。

### <a name="remarks"></a>备注

检索指向当前`ComPtrRef`对象表示的接口的指针。

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef：：运算符 T*

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator T*();
```

### <a name="remarks"></a>备注

返回当前`ComPtrRef`对象的[ptr_](comptrrefbase-class.md#ptr)数据成员的值。

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef：：操作员空隙\*\*

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator void**() const;
```

### <a name="remarks"></a>备注

删除当前`ComPtrRef`对象，将指向`ComPtrRef`该对象表示的接口的指针转换为指针到`void`指针到 ，然后返回强制转换指针。

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>Comptrref：：发布和获取地址

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>返回值

指向已删除`ComPtrRef`对象表示的接口的指针。

### <a name="remarks"></a>备注

删除当前`ComPtrRef`对象，并返回指向对象表示的接口的`ComPtrRef`指针指向指针。
