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
ms.openlocfilehash: f92a3e14018cf8c02dec40b664b72a0956f6220e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220530"
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
[ComPtr \<T> ](comptr-class.md)类型或从其派生的类型，而不仅仅是由表示的接口 `ComPtr` 。

## <a name="remarks"></a>备注

表示对类型的对象的引用 `ComPtr<T>` 。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                               | 描述
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef：： ComPtrRef](#comptrref) | `ComPtrRef`从指向其他对象的指定指针初始化类的新实例 `ComPtrRef` 。

### <a name="public-methods"></a>公共方法

“属性”                                                         | 描述
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef：： GetAddressOf](#getaddressof)                     | 检索指向当前对象表示的接口的指针的地址 `ComPtrRef` 。
[ComPtrRef：： ReleaseAndGetAddressOf](#releaseandgetaddressof) | 删除当前 `ComPtrRef` 对象，并返回指向由对象表示的接口的指针到指针 `ComPtrRef` 。

### <a name="public-operators"></a>公共运算符

名称                                                                     | 描述
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef：： operator InterfaceType * *](#operator-interfacetype-star-star) | 删除当前 `ComPtrRef` 对象，并返回指向由对象表示的接口的指针到指针 `ComPtrRef` 。
[ComPtrRef：： operator T *](#operator-t-star)                               | 返回当前 ComPtrRef 对象的[ptr_](comptrrefbase-class.md#ptr)数据成员的值。
[ComPtrRef：： operator void * *](#operator-void-star-star)                   | 删除当前 `ComPtrRef` 对象，将指针转换为由对象表示的接口，并将其转换为指针 `ComPtrRef` **`void`** ，然后返回 cast 指针。
[ComPtrRef：： operator *](#operator-star)                                   | 检索指向当前对象表示的接口的指针 `ComPtrRef` 。
[ComPtrRef：： operator = =](#operator-equality)                              | 指示两个 `ComPtrRef` 对象是否相等。
[ComPtrRef：： operator！ =](#operator-inequality)                            | 指示两个 `ComPtrRef` 对象是否不相等。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>ComPtrRef：： ComPtrRef

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>参数

*ptr*<br/>
另一对象的基础值 `ComPtrRef` 。

### <a name="remarks"></a>备注

`ComPtrRef`从指向其他对象的指定指针初始化类的新实例 `ComPtrRef` 。

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef：： GetAddressOf

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>返回值

指向由当前对象表示的接口的指针的地址 `ComPtrRef` 。

### <a name="remarks"></a>备注

检索指向当前对象表示的接口的指针的地址 `ComPtrRef` 。

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef：： operator = =

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

*的*<br/>
对 `ComPtrRef` 对象的引用。

*b*<br/>
对另一对象的引用 `ComPtrRef` ，或指向匿名类型（）的指针 **`void*`** 。

### <a name="return-value"></a>返回值

**`true`** 如果对象*a*等于对象*b*，则第一个运算符将生成; 否则为 **`false`** 。

第二个和第三个运算符在 **`true`** 对象*a*等于时生成 **`nullptr`** ; 否则为 **`false`** 。

**`true`** 如果对象*a*等于对象*b*，则第四个和第五个运算符将生成; 否则为 **`false`** 。

### <a name="remarks"></a>备注

指示两个 `ComPtrRef` 对象是否相等。

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef：： operator！ =

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

*的*<br/>
对 `ComPtrRef` 对象的引用。

*b*<br/>
对另一对象的引用 `ComPtrRef` ，或指向匿名对象（）的指针 **`void*`** 。

### <a name="return-value"></a>返回值

**`true`** 如果对象*a*不等于对象*b*，则第一个运算符将生成; 否则返回 **`false`** 。

**`true`** 如果对象*a*不等于，则第二个和第三个运算符将生成 **`nullptr`** ; 否则为 **`false`** 。

**`true`** 如果对象*a*不等于对象*b*，则第四个和第五个运算符将生成; 否则返回 **`false`** 。

### <a name="remarks"></a>备注

指示两个 `ComPtrRef` 对象是否不相等。

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef：： operator InterfaceType\*\*

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>备注

删除当前 `ComPtrRef` 对象，并返回指向由对象表示的接口的指针到指针 `ComPtrRef` 。

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef：： operator *

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>返回值

指向由当前对象表示的接口的指针 `ComPtrRef` 。

### <a name="remarks"></a>备注

检索指向当前对象表示的接口的指针 `ComPtrRef` 。

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef：： operator T *

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator T*();
```

### <a name="remarks"></a>备注

返回当前对象的[ptr_](comptrrefbase-class.md#ptr)数据成员的值 `ComPtrRef` 。

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef：： operator void\*\*

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator void**() const;
```

### <a name="remarks"></a>备注

删除当前 `ComPtrRef` 对象，将指针转换为由对象表示的接口，并将其转换为指针 `ComPtrRef` **`void`** ，然后返回 cast 指针。

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtrRef：： ReleaseAndGetAddressOf

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>返回值

指向已删除对象表示的接口的指针 `ComPtrRef` 。

### <a name="remarks"></a>备注

删除当前 `ComPtrRef` 对象，并返回指向由对象表示的接口的指针到指针 `ComPtrRef` 。
