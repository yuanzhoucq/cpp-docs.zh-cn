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
ms.openlocfilehash: 281e02d85e70a84530e6980d31669a73091448d5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784006"
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
一个[ComPtr\<T >](comptr-class.md)类型派生自它，而不仅仅是所表示接口`ComPtr`。

## <a name="remarks"></a>备注

表示类型的对象的引用`ComPtr<T>`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                               | 描述
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef::ComPtrRef](#comptrref) | 初始化的新实例`ComPtrRef`类从指定的指针到另一个`ComPtrRef`对象。

### <a name="public-methods"></a>公共方法

名称                                                         | 描述
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::GetAddressOf](#getaddressof)                     | 检索指向当前所表示接口的指针的地址`ComPtrRef`对象。
[ComPtrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | 删除当前`ComPtrRef`对象并返回到由表示的接口的指针到-的指针`ComPtrRef`对象。

### <a name="public-operators"></a>公共运算符

名称                                                                     | 描述
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Comptrref:: Operator InterfaceType * *](#operator-interfacetype-star-star) | 删除当前`ComPtrRef`对象并返回到由表示的接口的指针到-的指针`ComPtrRef`对象。
[Comptrref:: Operator T *](#operator-t-star)                               | 返回的值[ptr_](comptrrefbase-class.md#ptr)当前 ComPtrRef 对象的数据成员。
[Comptrref:: Operator void * *](#operator-void-star-star)                   | 删除当前`ComPtrRef`对象，将强制转换到由表示的接口指针`ComPtrRef`对象作为指针-到-指针-到`void`，然后返回强制转换指针。
[ComPtrRef::operator*](#operator-star)                                   | 检索指向当前所表示接口的指针`ComPtrRef`对象。
[ComPtrRef::operator==](#operator-equality)                              | 指示两个 `ComPtrRef` 对象是否相等。
[ComPtrRef::operator!=](#operator-inequality)                            | 指示两个 `ComPtrRef` 对象是否不相等。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL::Details

## <a name="comptrref"></a>ComPtrRef::ComPtrRef

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>参数

*ptr*<br/>
基础值的另一个`ComPtrRef`对象。

### <a name="remarks"></a>备注

初始化的新实例`ComPtrRef`类从指定的指针到另一个`ComPtrRef`对象。

## <a name="getaddressof"></a>ComPtrRef::GetAddressOf

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>返回值

指向当前所表示接口的指针的地址`ComPtrRef`对象。

### <a name="remarks"></a>备注

检索指向当前所表示接口的指针的地址`ComPtrRef`对象。

## <a name="operator-equality"></a>Comptrref:: Operator = =

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

*b*<br/>
对另一个引用`ComPtrRef`对象或到匿名类型的指针 (`void*`)。

### <a name="return-value"></a>返回值

第一个运算符产生 **，则返回 true**如果对象是否等于对象*b*; 否则为**false**。

第二个和第三个运算符会产生 **，则返回 true**如果对象等于**nullptr**; 否则为**false**。

第四个和第五个运算符会产生 **，则返回 true**如果对象是否等于对象*b*; 否则为**false**。

### <a name="remarks"></a>备注

指示两个 `ComPtrRef` 对象是否相等。

## <a name="operator-inequality"></a>ComPtrRef::operator!=

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

*b*<br/>
对另一个引用`ComPtrRef`对象或指向的匿名对象的指针 (`void*`)。

### <a name="return-value"></a>返回值

第一个运算符产生 **，则返回 true**如果对象不等于对象*b*; 否则为**false**。

第二个和第三个运算符会产生 **，则返回 true**如果对象是否不等于**nullptr**; 否则为**false**。

第四个和第五个运算符会产生 **，则返回 true**如果对象不等于对象*b*; 否则为**false**。

### <a name="remarks"></a>备注

指示两个 `ComPtrRef` 对象是否不相等。

## <a name="operator-interfacetype-star-star"></a>Comptrref:: Operator InterfaceType * *

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>备注

删除当前`ComPtrRef`对象并返回到由表示的接口的指针到-的指针`ComPtrRef`对象。

## <a name="operator-star"></a>ComPtrRef::operator*

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>返回值

指向由当前的接口`ComPtrRef`对象。

### <a name="remarks"></a>备注

检索指向当前所表示接口的指针`ComPtrRef`对象。

## <a name="operator-t-star"></a>Comptrref:: Operator T *

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator T*();
```

### <a name="remarks"></a>备注

返回的值[ptr_](comptrrefbase-class.md#ptr)数据成员的当前`ComPtrRef`对象。

## <a name="operator-void-star-star"></a>Comptrref:: Operator void\*\*

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator void**() const;
```

### <a name="remarks"></a>备注

删除当前`ComPtrRef`对象，将强制转换到由表示的接口指针`ComPtrRef`对象作为指针-到-指针-到`void`，然后返回强制转换指针。

## <a name="releaseandgetaddressof"></a>ComPtrRef::ReleaseAndGetAddressOf

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>返回值

指向表示的接口的已删除`ComPtrRef`对象。

### <a name="remarks"></a>备注

删除当前`ComPtrRef`对象并返回到由表示的接口的指针到-的指针`ComPtrRef`对象。
