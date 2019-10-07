---
title: ComPtr 类
ms.date: 07/26/2019
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
ms.openlocfilehash: 1e20a991c8f32027aeea6a17df0534aa6e1c2c43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498411"
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
`ComPtr`表示的接口。

*U*<br/>
当前`ComPtr`为其友元的类。 （使用此参数的模板受到保护。）

## <a name="remarks"></a>备注

`ComPtr<>`声明表示基础接口指针的类型。 使用`ComPtr<>`声明变量, 然后使用箭头成员访问运算符 (`->`) 访问接口成员函数。

有关智能指针的详细信息, 请参阅 MSDN Library 中[Com 编码实践](/windows/win32/LearnWin32/com-coding-practices)主题的 "Com 智能指针" 部分。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

name            | 描述
--------------- | ---------------------------------------------------------------
`InterfaceType` | *T*模板参数指定的类型的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                             | 描述
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | 初始化 `ComPtr` 类的新实例。 重载提供默认、复制、移动和转换构造函数。
[ComPtr::~ComPtr](#tilde-comptr) | 取消初始化的实例`ComPtr`。

### <a name="public-methods"></a>公共方法

名称                                                      | 描述
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: As](#as)                                         | 返回表示由指定模板参数标识的接口的对象。`ComPtr`
[ComPtr::AsIID](#asiid)                                   | 返回一个`ComPtr`对象, 该对象表示由指定接口 ID 标识的接口。
[ComPtr::AsWeak](#asweak)                                 | 检索对当前对象的弱引用。
[ComPtr::Attach](#attach)                                 | 将此`ComPtr`与当前模板类型参数指定的接口类型相关联。
[ComPtr::CopyTo](#copyto)                                 | 将与此`ComPtr`关联的当前或指定接口复制到指定的输出指针。
[ComPtr::Detach](#detach)                                 | 将此`ComPtr`与它所表示的接口解除。
[ComPtr::Get](#get)                                       | 检索指向与此`ComPtr`相关联的接口的指针。
[ComPtr::GetAddressOf](#getaddressof)                     | 检索[ptr_](#ptr)数据成员的地址, 其中包含指向此`ComPtr`所表示的接口的指针。
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | 释放与此`ComPtr`关联的接口, 然后检索[ptr_](#ptr)数据成员的地址, 其中包含指向已释放接口的指针。
[ComPtr::Reset](#reset)                                   | 释放指向与此`ComPtr`相关联的接口的指针的所有引用。
[ComPtr::Swap](#swap)                                     | 使用由指定`ComPtr`的管理的接口`ComPtr`交换由当前管理的接口。

### <a name="protected-methods"></a>受保护的方法

名称                                        | 描述
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | 递增与此`ComPtr`相关联的接口的引用计数。
[ComPtr::InternalRelease](#internalrelease) | 对与此`ComPtr`关联的接口执行 COM 释放操作。

### <a name="public-operators"></a>公共运算符

名称                                                                                           | 描述
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator&](#operator-ampersand)                                                       | 检索当前`ComPtr`的地址。
[ComPtr::operator->](#operator-arrow)                                                          | 检索指向当前模板参数所指定类型的指针。
[ComPtr::operator=](#operator-assign)                                                          | 为当前`ComPtr`赋值。
[ComPtr::operator==](#operator-equality)                                                       | 指示两个 `ComPtr` 对象是否相等。
[ComPtr::operator!=](#operator-inequality)                                                     | 指示两个 `ComPtr` 对象是否不相等。
[ComPtr:: operator Microsoft:: WRL::D etails:: BoolType](#operator-microsoft-wrl-details-booltype) | 指示是否`ComPtr`正在管理接口的对象生存期。

### <a name="protected-data-members"></a>受保护的数据成员

name                 | 描述
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | 包含指向与关联的接口的指针, 并由此管理`ComPtr`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtr`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft:: WRL

## <a name="tilde-comptr"></a>ComPtr:: ~ ComPtr

取消初始化的实例`ComPtr`。

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr:: As

返回表示由指定模板参数标识的接口的对象。`ComPtr`

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
要由参数*p*表示的接口。

*p*<br/>
一个`ComPtr`对象, 该对象表示由参数*U*指定的接口。参数*p*不得引用当前`ComPtr`对象。

### <a name="remarks"></a>备注

第一个模板是应在代码中使用的表单。 第二个模板是支持 [自动](../../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="asiid"></a>ComPtr:: AsIID

返回一个`ComPtr`对象, 该对象表示由指定接口 ID 标识的接口。

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
如果对象的某个接口的 ID 等于*riid*, 则为由*riid*参数指定的接口的双重间接指针;否则为指向`IUnknown`的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="asweak"></a>ComPtr:: AsWeak

检索对当前对象的弱引用。

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>参数

*pWeakRef*<br/>
此操作完成后, 指向弱引用对象的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="attach"></a>ComPtr:: Attach

将此`ComPtr`与当前模板类型参数指定的接口类型相关联。

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
   typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);

WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);

template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other, typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);
```

### <a name="parameters"></a>参数

*U*<br/>
*其他*参数的类型。

*other*<br/>
类型*U*的对象。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

第一个构造函数是默认构造函数, 隐式创建一个空对象。 第二个构造函数指定[__nullptr](../../extensions/nullptr-cpp-component-extensions.md), 它显式创建一个空对象。

第三个构造函数从指针指定的对象创建一个对象。 现在, ComPtr 拥有指向的内存, 并对其维护引用计数。

第四个和第五个构造函数是复制构造函数。 如果对象可转换为当前类型, 则第五个构造函数将复制该对象。

第六个和第七个构造函数是移动构造函数。 如果对象可转换为当前类型, 则第七个构造函数将移动该对象。

## <a name="copyto"></a>ComPtr:: CopyTo

将与此`ComPtr`关联的当前或指定接口复制到指定指针。

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
此操作完成后, 指向所请求的接口的指针。

*riid*<br/>
接口 ID。

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK;否则, 为一个 HRESULT, 指示隐式`QueryInterface`操作失败的原因。

### <a name="remarks"></a>备注

第一个函数返回指向与此`ComPtr`相关联的接口的指针的副本。 此函数始终返回 S_OK。

第二个函数对`QueryInterface`由*riid*参数指定的接口上`ComPtr`的与此关联的接口执行操作。

第三个函数对`QueryInterface` *U*参数的基础接口上与`ComPtr`此关联的接口执行操作。

## <a name="detach"></a>ComPtr::Detach

将此`ComPtr`对象与它所表示的接口解除。

```cpp
T* Detach();
```

### <a name="return-value"></a>返回值

指向由此`ComPtr`对象表示的接口的指针。

## <a name="get"></a>ComPtr:: Get

检索指向与此`ComPtr`相关联的接口的指针。

```cpp
T* Get() const;
```

### <a name="return-value"></a>返回值

指向与此`ComPtr`关联的接口的指针。

## <a name="getaddressof"></a>ComPtr::GetAddressOf

检索[ptr_](#ptr)数据成员的地址, 其中包含指向此`ComPtr`所表示的接口的指针。

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>返回值

变量的地址。

## <a name="internaladdref"></a>ComPtr::InternalAddRef

递增与此`ComPtr`相关联的接口的引用计数。

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>备注

此方法是受保护的。

## <a name="internalrelease"></a>ComPtr::InternalRelease

对与此`ComPtr`关联的接口执行 COM 释放操作。

```cpp
void InternalRelease();
```

### <a name="remarks"></a>备注

此方法是受保护的。

## <a name="operator-ampersand"></a>ComPtr::operator&amp;

释放与此`ComPtr`对象关联的接口, 然后检索`ComPtr`对象的地址。

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>返回值

对当前`ComPtr`的弱引用。

### <a name="remarks"></a>备注

此方法与[ComPtr:: GetAddressOf](#getaddressof)的不同之处在于, 此方法释放了对接口指针的引用。 在`ComPtr::GetAddressOf`需要接口指针的地址但不希望释放该接口时使用。

## <a name="operator-arrow"></a>ComPtr:: operator-&gt;

检索指向当前模板参数所指定类型的指针。

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>返回值

指向由当前模板类型名称指定的类型的指针。

### <a name="remarks"></a>备注

此 helper 函数消除了使用 STDMETHOD 宏引起的不必要的开销。 此函数将`IUnknown`生成`private`类型, `virtual`而不是。

## <a name="operator-assign"></a>ComPtr:: operator =

为当前`ComPtr`赋值。

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
对类型或其他`ComPtr`类型的指针、引用或右值引用。

### <a name="return-value"></a>返回值

对当前`ComPtr`的引用。

### <a name="remarks"></a>备注

此运算符的第一个版本将空值赋给当前`ComPtr`。

在第二个版本中, 如果分配接口指针与当前`ComPtr`接口指针不同, 则会将第二个接口指针分配给当前。 `ComPtr`

在第三个版本中, 分配接口指针分配给当前`ComPtr`。

在第四个版本中, 如果指定值的接口指针与当前`ComPtr`接口指针不同, 则会将第二个接口指针分配给当前。 `ComPtr`

第五个版本是复制运算符;对的`ComPtr`引用将分配给当前`ComPtr`。

第六个版本是使用移动语义的 copy 运算符;如果任何类型为静态`ComPtr`强制转换, 然后将其分配给当前`ComPtr`, 则为对的右值引用。

第七个版本是使用移动语义的 copy 运算符;对`ComPtr`类型*U*的右值引用是静态强制转换, 并分配给当前`ComPtr`。

## <a name="operator-equality"></a>ComPtr:: operator = =

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
对另一`ComPtr`对象的引用。

### <a name="return-value"></a>返回值

如果对象*a*等于`true`对象*b*, `false`则第一个运算符将生成; 否则为。

第二个和第三`true`个运算符在对象*a*等于`nullptr`时生成; `false`否则为。

## <a name="operator-inequality"></a>ComPtr:: operator! =

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
对另一`ComPtr`对象的引用。

### <a name="return-value"></a>返回值

如果对象*a*不`true`等于对象*b*, `false`则第一个运算符将生成; 否则返回。

如果对象*a*不等于`nullptr`, `true`则第二个和第三个运算符将`false`生成; 否则为。

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr:: operator Microsoft:: WRL::D etails:: BoolType

指示是否`ComPtr`正在管理接口的对象生存期。

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>返回值

如果接口与此`ComPtr`关联, 则为[BoolStruct:: member](boolstruct-structure.md#member)数据`nullptr`成员的地址; 否则为。

## <a name="ptr"></a>ComPtr::p tr_

包含指向与关联的接口的指针, 并由此管理`ComPtr`。

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>备注

`ptr_`是受保护的内部数据成员。

## <a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

释放与此`ComPtr`关联的接口, 然后检索[ptr_](#ptr)数据成员的地址, 其中包含指向已释放接口的指针。

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>返回值

此`ComPtr`的[ptr_](#ptr)数据成员的地址。

## <a name="reset"></a>ComPtr:: Reset

释放指向与此`ComPtr`相关联的接口的指针的所有引用。

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>返回值

已释放的引用的数量（如果存在）。

## <a name="swap"></a>ComPtr:: Swap

使用由指定`ComPtr`的管理的接口`ComPtr`交换由当前管理的接口。

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

