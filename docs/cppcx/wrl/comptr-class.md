---
title: ComPtr 类
ms.date: 10/01/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
- client/Microsoft::WRL::ComPtr::As
- client/Microsoft::WRL::ComPtr::AsIID
- client/Microsoft::WRL::ComPtr::AsWeak
- client/Microsoft::WRL::ComPtr::Attach
- client/Microsoft::WRL::ComPtr::ComPtr
- client/Microsoft::WRL::ComPtr::CopyTo
- client/Microsoft::WRL::ComPtr::Detach
- client/Microsoft::WRL::ComPtr::Get
- client/Microsoft::WRL::ComPtr::GetAddressOf
- client/Microsoft::WRL::ComPtr::InternalAddRef
- client/Microsoft::WRL::ComPtr::InternalRelease
- client/Microsoft::WRL::ComPtr::operator&
- client/Microsoft::WRL::ComPtr::operator->
- client/Microsoft::WRL::ComPtr::operator=
- client/Microsoft::WRL::ComPtr::operator==
- client/Microsoft::WRL::ComPtr::operator!=
- client/Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType
- client/Microsoft::WRL::ComPtr::ptr_
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
- client/Microsoft::WRL::ComPtr::Reset
- client/Microsoft::WRL::ComPtr::Swap
- client/Microsoft::WRL::ComPtr::~ComPtr
helpviewer_keywords:
- Microsoft::WRL::ComPtr class
- Microsoft::WRL::ComPtr::As method
- Microsoft::WRL::ComPtr::AsIID method
- Microsoft::WRL::ComPtr::AsWeak method
- Microsoft::WRL::ComPtr::Attach method
- Microsoft::WRL::ComPtr::ComPtr, constructor
- Microsoft::WRL::ComPtr::CopyTo method
- Microsoft::WRL::ComPtr::Detach method
- Microsoft::WRL::ComPtr::Get method
- Microsoft::WRL::ComPtr::GetAddressOf method
- Microsoft::WRL::ComPtr::InternalAddRef method
- Microsoft::WRL::ComPtr::InternalRelease method
- Microsoft::WRL::ComPtr::operator& operator
- Microsoft::WRL::ComPtr::operator-> operator
- Microsoft::WRL::ComPtr::operator= operator
- Microsoft::WRL::ComPtr::operator== operator
- Microsoft::WRL::ComPtr::operator!= operator
- Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType operator
- Microsoft::WRL::ComPtr::ptr_ data member
- Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf method
- Microsoft::WRL::ComPtr::Reset method
- Microsoft::WRL::ComPtr::Swap method
- Microsoft::WRL::ComPtr::~ComPtr, destructor
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
ms.openlocfilehash: 9e5b2419f070ead17e72b1642f510f74bad8260e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398675"
---
# <a name="comptr-class"></a>ComPtr 类

创建表示模板参数指定的接口的 *智能指针* 类型。 `ComPtr` 会自动维护基础接口指针的引用计数，并在引用计数变为零时发布接口。

## <a name="syntax"></a>语法

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>参数

*T*<br/>
该接口的`ComPtr`表示。

*U*<br/>
将类传递给其当前`ComPtr`为友元。 （使用此参数的模板受到保护。）

## <a name="remarks"></a>备注

`ComPtr<>` 声明表示基础接口指针的类型。 使用`ComPtr<>`声明一个变量，然后使用箭头成员访问运算符 (`->`) 访问接口成员函数。

有关智能指针的详细信息，请参阅"COM 智能指针"部分[COM Coding Practices](/windows/desktop/LearnWin32/com-coding-practices) MSDN Library 中的主题。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称            | 描述
--------------- | ---------------------------------------------------------------
`InterfaceType` | 指定的类型的同义词*T*模板参数。

### <a name="public-constructors"></a>公共构造函数

名称                             | 描述
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | 初始化 `ComPtr` 类的新实例。 重载提供默认、复制、移动和转换构造函数。
[ComPtr::~ComPtr](#tilde-comptr) | 取消初始化的实例`ComPtr`。

### <a name="public-methods"></a>公共方法

名称                                                      | 描述
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::As](#as)                                         | 返回`ComPtr`对象，表示由指定的模板参数标识的接口。
[ComPtr::AsIID](#asiid)                                   | 返回`ComPtr`对象，表示由指定的接口 ID 标识的接口
[ComPtr::AsWeak](#asweak)                                 | 检索对当前对象的弱引用。
[ComPtr::Attach](#attach)                                 | 将相关联这`ComPtr`与由当前模板类型参数指定的接口类型。
[ComPtr::CopyTo](#copyto)                                 | 将复制与此相关联的当前或指定界面`ComPtr`到指定的输出指针。
[ComPtr::Detach](#detach)                                 | 取消关联这`ComPtr`从它所代表的接口。
[ComPtr::Get](#get)                                       | 检索指向与此相关联的接口的`ComPtr`。
[ComPtr::GetAddressOf](#getaddressof)                     | 检索的地址[ptr_](#ptr)数据成员，其中包含指向此所表示接口`ComPtr`。
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | 释放与此关联的接口`ComPtr`，然后检索的地址[ptr_](#ptr)数据成员，其中包含指向已释放接口的指针。
[ComPtr::Reset](#reset)                                   | 释放对与此相关联的接口指针的所有引用`ComPtr`。
[ComPtr::Swap](#swap)                                     | 交换当前管理的接口`ComPtr`管理指定的接口与`ComPtr`。

### <a name="protected-methods"></a>受保护的方法

名称                                        | 描述
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | 递增与此相关联的接口的引用计数`ComPtr`。
[ComPtr::InternalRelease](#internalrelease) | 执行与此相关联的接口上的 COM 释放操作`ComPtr`。

### <a name="public-operators"></a>公共运算符

名称                                                                                           | 描述
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator&](#operator-ampersand)                                                       | 检索当前的地址`ComPtr`。
[ComPtr::operator->](#operator-arrow)                                                          | 检索指向当前模板参数所指定类型的指针。
[ComPtr::operator=](#operator-assign)                                                          | 将值分配给当前`ComPtr`。
[ComPtr::operator==](#operator-equality)                                                       | 指示两个 `ComPtr` 对象是否相等。
[ComPtr::operator!=](#operator-inequality)                                                     | 指示两个 `ComPtr` 对象是否不相等。
[Comptr:: Operator Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | 指示是否`ComPtr`管理接口的对象生存期。

### <a name="protected-data-members"></a>受保护的数据成员

name                 | 描述
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | 包含指向相关联，并管理此接口的指针`ComPtr`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtr`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft:: wrl

## <a name="tilde-comptr"></a>ComPtr::~ComPtr

取消初始化的实例`ComPtr`。

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>Comptr:: As

返回`ComPtr`对象，表示由指定的模板参数标识的接口。

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>参数

*U*<br/>
要由参数表示的接口*p*。

*p*<br/>
一个`ComPtr`对象，表示指定参数的接口*U*。参数*p*必须引用当前`ComPtr`对象。

### <a name="remarks"></a>备注

第一个模板是应在代码中使用的表单。 第二个模板是支持 [自动](../../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="asiid"></a>ComPtr::AsIID

返回`ComPtr`对象，表示由指定的接口 ID 标识的接口

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*p*<br/>
如果对象具有的接口 ID 等于*riid*，指向由指定的接口的双向间接指针*riid*参数; 否则为一个指向`IUnknown`。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="asweak"></a>Comptr:: Asweak

检索对当前对象的弱引用。

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>参数

*pWeakRef*<br/>
此操作完成后，指向弱引用对象的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="attach"></a>ComPtr::Attach

将相关联这`ComPtr`与由当前模板类型参数指定的接口类型。

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>参数

*other*<br/>
接口类型。

## <a name="comptr"></a>ComPtr::ComPtr

初始化 `ComPtr` 类的新实例。 重载提供默认、复制、移动和转换构造函数。

```cpp
WRL_NOTHROW ComPtr();
WRL_NOTHROW ComPtr(
   decltype(__nullptr)
);
template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr(
   const ComPtr& other
);
template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>参数

*U*<br/>
类型*其他*参数。

*other*<br/>
类型的对象*U*。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

第一个构造函数是默认构造函数，哪些隐式创建一个空的对象。 第二个构造函数指定[__nullptr](../../extensions/nullptr-cpp-component-extensions.md)，其显式创建一个空的对象。

第三个构造函数创建从指针指定的对象的对象。

第四个和第五个构造函数是复制构造函数。 第五个构造函数将对象转换为当前类型的情况下将其复制。

第六个和第七个构造函数是移动构造函数。 第七个构造函数移动对象，如果转换为当前的类型。

## <a name="copyto"></a>ComPtr::CopyTo

将复制与此相关联的当前或指定界面`ComPtr`到指定的指针。

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>参数

*U*<br/>
类型名称。

*ptr*<br/>
此操作完成后，指向所请求的接口的指针。

*riid*<br/>
接口 ID。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为一个 HRESULT，指示原因的隐式`QueryInterface`操作失败。

### <a name="remarks"></a>备注

在第一个函数返回与此相关联的接口的指针的副本`ComPtr`。 此函数始终返回 S_OK。

第二个函数执行`QueryInterface`与此相关联的接口上的操作`ComPtr`为指定的接口*riid*参数。

第三个函数执行`QueryInterface`与此相关联的接口上的操作`ComPtr`基础接口*U*参数。

## <a name="detach"></a>ComPtr::Detach

取消关联这`ComPtr`从它所代表的接口的对象。

```cpp
T* Detach();
```

### <a name="return-value"></a>返回值

指向表示此接口的指针`ComPtr`对象。

## <a name="get"></a>ComPtr::Get

检索指向与此相关联的接口的`ComPtr`。

```cpp
T* Get() const;
```

### <a name="return-value"></a>返回值

指向与此相关联的接口`ComPtr`。

## <a name="getaddressof"></a>ComPtr::GetAddressOf

检索的地址[ptr_](#ptr)数据成员，其中包含指向此所表示接口`ComPtr`。

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>返回值

变量的地址。

## <a name="internaladdref"></a>ComPtr::InternalAddRef

递增与此相关联的接口的引用计数`ComPtr`。

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>备注

此方法受到保护。

## <a name="internalrelease"></a>ComPtr::InternalRelease

执行与此相关联的接口上的 COM 释放操作`ComPtr`。

```cpp
void InternalRelease();
```

### <a name="remarks"></a>备注

此方法受到保护。

## <a name="operator-ampersand"></a>ComPtr::operator&amp;

释放与此关联的接口`ComPtr`对象，然后检索的地址`ComPtr`对象。

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>返回值

对当前的弱引用`ComPtr`。

### <a name="remarks"></a>备注

此方法不同于[comptr:: Getaddressof](#getaddressof) ，此方法释放接口指针的引用。 使用`ComPtr::GetAddressOf`时需要的接口指针的地址但不是想要发布该接口。

## <a name="operator-arrow"></a>ComPtr::operator-&gt;

检索指向当前模板参数所指定类型的指针。

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>返回值

指向当前模板类型名称由指定的类型。

### <a name="remarks"></a>备注

此帮助器函数删除由使用 STDMETHOD 宏导致不必要的开销。 此功能，可以`IUnknown`类型`private`而不是`virtual`。

## <a name="operator-assign"></a>ComPtr::operator=

将值分配给当前`ComPtr`。

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>参数

*U*<br/>
一个类。

*other*<br/>
指针、 引用或右值引用类型或另一`ComPtr`。

### <a name="return-value"></a>返回值

对当前的引用`ComPtr`。

### <a name="remarks"></a>备注

此运算符的第一个版本将为空值分配给当前`ComPtr`。

在第二个版本中，如果分配的接口指针不是与当前`ComPtr`的接口指针，第二个接口指针分配给当前`ComPtr`。

在第三个版本中，分配的接口指针分配给当前`ComPtr`。

在第四个版本中，如果分配值的接口指针不是与当前`ComPtr`的接口指针，第二个接口指针分配给当前`ComPtr`。

第五个版本是复制运算符;对引用`ComPtr`分配给当前`ComPtr`。

第六个版本是使用复制运算符移动语义;右值引用`ComPtr`如果任何类型是静态的强制转换，然后分配给当前`ComPtr`。

第七个版本是使用复制运算符移动语义;右值引用`ComPtr`类型的*U*是静态然后强制转换和分配给当前`ComPtr`。

## <a name="operator-equality"></a>Comptr:: Operator = =

指示两个 `ComPtr` 对象是否相等。

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>参数

*a*<br/>
对 `ComPtr` 对象的引用。

*b*<br/>
对另一个引用`ComPtr`对象。

### <a name="return-value"></a>返回值

第一个运算符产生`true`如果对象等同于对象*b*; 否则为`false`。

第二个和第三个运算符会产生`true`如果对象等于`nullptr`; 否则为`false`。

## <a name="operator-inequality"></a>Comptr:: Operator ！ =

指示两个 `ComPtr` 对象是否不相等。

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>参数

*a*<br/>
对 `ComPtr` 对象的引用。

*b*<br/>
对另一个引用`ComPtr`对象。

### <a name="return-value"></a>返回值

第一个运算符产生`true`如果对象不是等于对象*b*; 否则为`false`。

第二个和第三个运算符会产生`true`如果对象是否不等于`nullptr`; 否则为`false`。

## <a name="operator-microsoft-wrl-details-booltype"></a>Comptr:: Operator Microsoft::WRL::Details::BoolType

指示是否`ComPtr`管理接口的对象生存期。

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>返回值

如果接口与此相关联`ComPtr`的地址[boolstruct:: Member](boolstruct-structure.md#member)数据成员; 否则为`nullptr`。

## <a name="ptr"></a>ComPtr::ptr_

包含指向相关联，并管理此接口的指针`ComPtr`。

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>备注

`ptr_` 是一个内部、 受保护的数据成员。

## <a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

释放与此关联的接口`ComPtr`，然后检索的地址[ptr_](#ptr)数据成员，其中包含指向已释放接口的指针。

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>返回值

地址[ptr_](#ptr)数据成员`ComPtr`。

## <a name="reset"></a>ComPtr::Reset

释放对与此相关联的接口指针的所有引用`ComPtr`。

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>返回值

已释放的引用的数量（如果存在）。

## <a name="swap"></a>ComPtr::Swap

交换当前管理的接口`ComPtr`管理指定的接口与`ComPtr`。

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>参数

*r*<br/>
`ComPtr`。

