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
ms.openlocfilehash: 89c09ede972f5bdd5da1dde810cad31733bdf338
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372644"
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
表示的`ComPtr`接口。

*美国*<br/>
当前`ComPtr`是朋友的类。 （使用此参数的模板受到保护。）

## <a name="remarks"></a>备注

`ComPtr<>`声明表示基础接口指针的类型。 用于`ComPtr<>`声明变量，然后使用箭头成员访问运算符 （`->`） 访问接口成员函数。

有关智能指针的详细信息，请参阅 MSDN 库中 COM 编码实践主题的["COM](/windows/win32/LearnWin32/com-coding-practices)智能指针"小节。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称            | 说明
--------------- | ---------------------------------------------------------------
`InterfaceType` | *T*模板参数指定的类型的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                             | 说明
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr：ComPtr](#comptr)        | 初始化 `ComPtr` 类的新实例。 重载提供默认、复制、移动和转换构造函数。
[ComPtr：：*ComPtr](#tilde-comptr) | 取消初始化 的`ComPtr`实例。

### <a name="public-methods"></a>公共方法

名称                                                      | 说明
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr：如](#as)                                         | 返回表示`ComPtr`指定模板参数标识的接口的对象。
[ComPtr：：AsIID](#asiid)                                   | 返回表示`ComPtr`指定接口 ID 标识的接口的对象。
[ComPtr：：作为弱](#asweak)                                 | 检索对当前对象的弱引用。
[ComPtr：：附加](#attach)                                 | 将这与`ComPtr`当前模板类型参数指定的接口类型关联。
[Comptr：：复制到](#copyto)                                 | 将与此关联的当前或指定接口`ComPtr`复制到指定的输出指针。
[康普特：:D泰](#detach)                                 | 将其`ComPtr`与它所代表的接口分离。
[ComPtr：获取](#get)                                       | 检索指向与此关联的接口的指针`ComPtr`。
[Comptr：获取地址](#getaddressof)                     | 检索[ptr_](#ptr)数据成员的地址，其中包含指向此`ComPtr`表示的接口的指针。
[Comptr：：释放和获取地址](#releaseandgetaddressof) | 释放与此关联的接口，`ComPtr`然后检索[ptr_](#ptr)数据成员的地址，该地址包含指向释放的接口的指针。
[ComPtr::Reset](#reset)                                   | 释放指向与此`ComPtr`关联的接口的指针的所有引用。
[交流：：交换](#swap)                                     | 将当前`ComPtr`管理的接口与指定的`ComPtr`的接换。

### <a name="protected-methods"></a>受保护的方法

名称                                        | 说明
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr：：内部AddRef](#internaladdref)   | 增加与此关联的接口的引用计数`ComPtr`。
[ComPtr：：内部发布](#internalrelease) | 对与此关联的接口执行 COM 发布操作`ComPtr`。

### <a name="public-operators"></a>公共运算符

名称                                                                                           | 说明
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr：：操作员&](#operator-ampersand)                                                       | 检索当前`ComPtr`的地址。
[ComPtr：：操作员->](#operator-arrow)                                                          | 检索指向当前模板参数所指定类型的指针。
[ComPtr：：操作员*](#operator-assign)                                                          | 将值分配给当前`ComPtr`。
[通讯：：操作员*](#operator-equality)                                                       | 指示两个 `ComPtr` 对象是否相等。
[ComPtr：：操作员！](#operator-inequality)                                                     | 指示两个 `ComPtr` 对象是否不相等。
[ComPtr：：操作者微软：：WRL：:D尾：：布尔类型](#operator-microsoft-wrl-details-booltype) | 指示 是否`ComPtr`正在管理接口的对象生存期。

### <a name="protected-data-members"></a>受保护的数据成员

名称                 | 说明
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr：:ptr]](#ptr) | 包含指向与此关联的接口并由 其管理的指针`ComPtr`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtr`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr：：*ComPtr

取消初始化 的`ComPtr`实例。

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr：如

返回表示`ComPtr`指定模板参数标识的接口的对象。

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

*美国*<br/>
参数*p*表示的接口。

*P*<br/>
表示`ComPtr`参数*U*指定的接口的对象。参数*p*不能引用当前`ComPtr`对象。

### <a name="remarks"></a>备注

第一个模板是应在代码中使用的表单。 第二个模板是支持 [自动](../../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr：：AsIID

返回表示`ComPtr`指定接口 ID 标识的接口的对象。

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*P*<br/>
如果对象具有 ID 等于*riid*的接口，则指向*riid*参数指定的接口的双间接指针;否则，指向`IUnknown`的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr：：作为弱

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

## <a name="comptrattach"></a><a name="attach"></a>ComPtr：：附加

将这与`ComPtr`当前模板类型参数指定的接口类型关联。

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>参数

*其他*<br/>
接口类型。

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr：ComPtr

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

*美国*<br/>
*其他*参数的类型。

*其他*<br/>
*U*类型的对象 。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

第一个构造函数是默认构造函数，它突然创建一个空对象。 第二个构造函数指定[__nullptr](../../extensions/nullptr-cpp-component-extensions.md)，显式创建空对象。

第三个构造函数从指针指定的对象创建对象。 ComPtr 现在拥有指向的内存，并维护对它的引用计数。

第四个和第五个构造函数是复制构造函数。 如果对象可转换为当前类型，则第五个构造函数将复制该对象。

第六和第七构造函数是移动构造函数。 如果对象可转换为当前类型，则第七个构造函数将对象移动。

## <a name="comptrcopyto"></a><a name="copyto"></a>Comptr：：复制到

将与此关联的当前或指定接口`ComPtr`复制到指定的指针。

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

*美国*<br/>
类型名称。

*Ptr*<br/>
此操作完成后，将指向请求的接口的指针。

*riid*<br/>
接口 ID。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，指示隐式`QueryInterface`操作失败原因的 HRESULT。

### <a name="remarks"></a>备注

第一个函数返回指向与此`ComPtr`关联的接口的指针的副本。 此函数始终返回S_OK。

第二个`QueryInterface`函数`ComPtr`对*riid*参数指定的接口执行与此关联的接口的操作。

第三个`QueryInterface`函数`ComPtr`对*U*参数的基础接口执行与此关联的接口的操作。

## <a name="comptrdetach"></a><a name="detach"></a>康普特：:D泰

将此`ComPtr`对象与它所代表的接口分离。

```cpp
T* Detach();
```

### <a name="return-value"></a>返回值

指向此`ComPtr`对象表示的接口的指针。

## <a name="comptrget"></a><a name="get"></a>ComPtr：获取

检索指向与此关联的接口的指针`ComPtr`。

```cpp
T* Get() const;
```

### <a name="return-value"></a>返回值

指向与此关联的接口`ComPtr`的指针。

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>Comptr：获取地址

检索[ptr_](#ptr)数据成员的地址，其中包含指向此`ComPtr`表示的接口的指针。

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>返回值

变量的地址。

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr：：内部AddRef

增加与此关联的接口的引用计数`ComPtr`。

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>备注

此方法受到保护。

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr：：内部发布

对与此关联的接口执行 COM 发布操作`ComPtr`。

```cpp
void InternalRelease();
```

### <a name="remarks"></a>备注

此方法受到保护。

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr：：运算符&amp;

释放与此`ComPtr`对象关联的接口，然后检索`ComPtr`该对象的地址。

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>返回值

对电流`ComPtr`的弱引用。

### <a name="remarks"></a>备注

此方法不同于[ComPtr：：GetAddressof，](#getaddressof)因为此方法释放对接口指针的引用。 当您`ComPtr::GetAddressOf`需要接口指针的地址，但不希望释放该接口时使用。

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr：：操作员-&gt;

检索指向当前模板参数所指定类型的指针。

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>返回值

指向当前模板类型名称指定的类型。

### <a name="remarks"></a>备注

此帮助程序函数消除了由于使用 STDMETHOD 宏而导致的不必要的开销。 此函数使`IUnknown`类型`private`而不是`virtual`。

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr：：操作员*

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

*美国*<br/>
类。

*其他*<br/>
对类型或其他的指针、引用或 rvalue 引用`ComPtr`。

### <a name="return-value"></a>返回值

对当前`ComPtr`的引用。

### <a name="remarks"></a>备注

此运算符的第一个版本将空值分配给当前`ComPtr`。

在第二版本中，如果分配接口指针与当前`ComPtr`接口指针不同，则第二个接口指针将分配给当前`ComPtr`。

在第三个版本中，分配接口指针分配给当前`ComPtr`。

在第四版本中，如果分配值的接口指针与当前`ComPtr`接口指针不同，则第二个接口指针将分配给当前`ComPtr`。

第五个版本是复制运算符;对 的`ComPtr`引用分配给当前`ComPtr`。

第六个版本是使用移动语义的复制运算符;对 的`ComPtr`rvalue 引用，如果任何类型都是静态强制转换，然后`ComPtr`分配给当前 。

第七个版本是使用移动语义的复制运算符;对*类型 U* `ComPtr`的 rvalue 引用是静态强制转换，然后分配给`ComPtr`当前 。

## <a name="comptroperator"></a><a name="operator-equality"></a>通讯：：操作员*

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

*B*<br/>
对另一个`ComPtr`对象的引用。

### <a name="return-value"></a>返回值

如果对象`true`*a*等于对象*b，* 则第一个运算符将生成。否则， `false`.

如果对象*a*等于 ，则第二个`nullptr`和第三个运算符屈服`true`。否则， `false`.

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr：：操作员！

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

*B*<br/>
对另一个`ComPtr`对象的引用。

### <a name="return-value"></a>返回值

如果对象`true`*a*不等于对象*b，* 则第一个运算符将生成。否则， `false`.

如果对象*a*不等于 ，则第二个`nullptr`和第三个运算符屈服`true`。否则， `false`.

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr：：操作者微软：：WRL：:D尾：：布尔类型

指示 是否`ComPtr`正在管理接口的对象生存期。

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>返回值

如果接口与此关联`ComPtr`，则[BoolStruct 的地址：：成员](boolstruct-structure.md#member)数据成员;否则， `nullptr`.

## <a name="comptrptr_"></a><a name="ptr"></a>ComPtr：:ptr]

包含指向与此关联的接口并由 其管理的指针`ComPtr`。

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>备注

`ptr_`是内部受保护的数据成员。

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>Comptr：：释放和获取地址

释放与此关联的接口，`ComPtr`然后检索[ptr_](#ptr)数据成员的地址，该地址包含指向释放的接口的指针。

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>返回值

ptr_`ComPtr`[数据成员](#ptr)的地址。

## <a name="comptrreset"></a><a name="reset"></a>ComPtr：重置

释放指向与此`ComPtr`关联的接口的指针的所有引用。

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>返回值

已释放的引用的数量（如果存在）。

## <a name="comptrswap"></a><a name="swap"></a>交流：：交换

将当前`ComPtr`管理的接口与指定的`ComPtr`的接换。

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>参数

*R*<br/>
一个 `ComPtr`。
