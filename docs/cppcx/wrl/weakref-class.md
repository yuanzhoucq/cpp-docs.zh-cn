---
title: WeakRef 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
- client/Microsoft::WRL::WeakRef::~WeakRef
- client/Microsoft::WRL::WeakRef::As
- client/Microsoft::WRL::WeakRef::AsIID
- client/Microsoft::WRL::WeakRef::CopyTo
- client/Microsoft::WRL::WeakRef::operator&
- client/Microsoft::WRL::WeakRef::WeakRef
helpviewer_keywords:
- Microsoft::WRL::WeakRef class
- Microsoft::WRL::WeakRef::~WeakRef, destructor
- Microsoft::WRL::WeakRef::As method
- Microsoft::WRL::WeakRef::AsIID method
- Microsoft::WRL::WeakRef::CopyTo method
- Microsoft::WRL::WeakRef::operator& operator
- Microsoft::WRL::WeakRef::WeakRef, constructor
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
ms.openlocfilehash: 715a823784aaa75f9abe349ef0a7ddc9e5d607d1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218346"
---
# <a name="weakref-class"></a>WeakRef 类

表示只能由 Windows 运行时而不是经典 COM 使用的 *弱引用* 。 弱引用表示可能可访问或可能不可访问的对象。

## <a name="syntax"></a>语法

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[WeakRef::WeakRef 构造函数](#weakref)|初始化 `WeakRef` 类的新实例。|
|[WeakRef::~WeakRef 析构函数](#tilde-weakref)|取消初始化类的当前实例 `WeakRef` 。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[WeakRef::As 方法](#as)|设置指定的 `ComPtr` 指针参数以表示指定的接口。|
|[WeakRef::AsIID 方法](#asiid)|设置指定的 `ComPtr` 指针参数以表示指定的接口 ID。|
|[WeakRef::CopyTo 方法](#copyto)|如果可用，请为指定的指针变量分配一个指向接口的指针。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[WeakRef::operator& 运算符](#operator-ampersand-operator)|返回 `ComPtrRef` 表示当前对象的对象 `WeakRef` 。|

## <a name="remarks"></a>备注

`WeakRef`对象维护与对象相关联的*强引用*，该引用可以是有效的，也可以是无效的。 调用 `As()` 或 `AsIID()` 方法获取强引用。 如果强引用有效，就可以访问关联的对象。 如果强引用无效（ **`nullptr`** ），则不能访问关联的对象。

`WeakRef`对象通常用于表示由外部线程或应用程序控制其存在性的对象。 例如， `WeakRef` 通过对文件对象的引用构造对象。 文件打开时，强引用有效。 但文件关闭时，强引用无效。

请注意，Windows 10 SDK 中的 [As](#as)、 [AsIID](#asiid) 和 [CopyTo](#copyto) 方法中没有发生行为更改。 以前，在调用这些方法中的任何方法后，可以检查以 `WeakRef` **`nullptr`** 确定是否已成功获得强引用，如以下代码所示：

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)
{
    wprintf(L"Couldn’t get strong ref!");
}
```

使用 Windows 10 SDK（或更高版本）时以上代码无效。 而是检查为传入的指针 **`nullptr`** 。

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtr`

`WeakRef`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>WeakRef：： ~ WeakRef 析构函数

取消初始化类的当前实例 `WeakRef` 。

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>WeakRef：： As 方法

设置指定的 `ComPtr` 指针参数以表示指定的接口。

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>参数

*U*<br/>
接口 ID。

*ptr*<br/>
此操作完成后，表示参数*U*的对象。

### <a name="return-value"></a>返回值

- 如果此操作成功，则 S_OK;否则，为 HRESULT，指示操作失败的原因， *ptr*设置为 **`nullptr`** 。

- 如果此操作成功，但已释放当前对象，则 S_OK `WeakRef` 。 参数*ptr*设置为 **`nullptr`** 。

- S_OK 如果此操作成功，但当前 `WeakRef` 对象不是从参数*U*派生的，则为。参数*ptr*设置为 **`nullptr`** 。

### <a name="remarks"></a>备注

如果参数*U*为 `IWeakReference` ，或者不是从派生的，则会发出错误 `IInspectable` 。

第一个模板是应在代码中使用的表单。 第二个模板是支持 [自动](../../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

从 Windows 10 SDK 开始， `WeakRef` 如果无法获得弱引用，此方法不会将实例设置为 **`nullptr`** ，因此应避免检查的错误检查代码 `WeakRef` **`nullptr`** 。 相反，请*ptr*检查 ptr **`nullptr`** 。

## <a name="weakrefasiid-method"></a><a name="asiid"></a>WeakRef：： AsIID 方法

设置指定的 `ComPtr` 指针参数以表示指定的接口 ID。

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*ptr*<br/>
此操作完成后，表示参数*riid*的对象。

### <a name="return-value"></a>返回值

- 如果此操作成功，则 S_OK;否则，为 HRESULT，指示操作失败的原因， *ptr*设置为 **`nullptr`** 。

- 如果此操作成功，但已释放当前对象，则 S_OK `WeakRef` 。 参数*ptr*设置为 **`nullptr`** 。

- S_OK 如果此操作成功，但当前 `WeakRef` 对象不是从参数*riid*派生的，则为。 参数*ptr*设置为 **`nullptr`** 。 (有关更多信息，请参阅“备注”。)

### <a name="remarks"></a>备注

如果参数*riid*不是从派生的，则会发出错误 `IInspectable` 。 此错误将取代返回值。

第一个模板是应在代码中使用的表单。 第二个模板（此处未显示，但在头文件中声明）是支持 [自动](../../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

从 Windows 10 SDK 开始， `WeakRef` 如果无法获得弱引用，此方法不会将实例设置为 **`nullptr`** ，因此应避免检查的错误检查代码 `WeakRef` **`nullptr`** 。 相反，请*ptr*检查 ptr **`nullptr`** 。

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>WeakRef：： CopyTo 方法

如果可用，请为指定的指针变量分配一个指向接口的指针。

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>参数

*U*<br/>
指向接口的指针 `IInspectable` 。 如果*U*不是从派生的，则会发出错误 `IInspectable` 。

*riid*<br/>
接口 ID。 如果*riid*不是从派生的，则会发出错误 `IWeakReference` 。

*ptr*<br/>
指向或的双向间接指针 `IInspectable` `IWeakReference` 。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。 有关详细信息，请参阅 "**备注**"。

### <a name="remarks"></a>备注

返回值 S_OK 表示此操作成功，但并不指示弱引用是否解析为强引用。 如果返回 S_OK，则测试参数*p*是否为强引用;也就是说，参数*p*不等于 **`nullptr`** 。

从 Windows 10 SDK 开始， `WeakRef` 如果无法获得弱引用，此方法不会将实例设置为 **`nullptr`** ，因此应避免检查的错误检查代码 `WeakRef` **`nullptr`** 。 相反，请*ptr*检查 ptr **`nullptr`** 。

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>WeakRef：： operator &amp; 运算符

返回 `ComPtrRef` 表示当前对象的对象 `WeakRef` 。

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>返回值

一个 `ComPtrRef` 表示当前对象的对象 `WeakRef` 。

### <a name="remarks"></a>备注

这是一个内部 helper 运算符，不应在代码中使用。

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>WeakRef：： WeakRef 构造函数

初始化 `WeakRef` 类的新实例。

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>参数

*ptr*<br/>
对初始化当前对象的现有对象的指针、引用或右值引用 `WeakRef` 。

### <a name="remarks"></a>备注

第一个构造函数初始化一个空的 `WeakRef` 对象。 第二个构造函数 `WeakRef` 从指向接口的指针初始化一个对象 `IWeakReference` 。 第三个构造函数 `WeakRef` 从对对象的引用初始化对象 `ComPtr<IWeakReference>` 。 第四个和第五个构造函数 `WeakRef` 从另一个对象初始化一个对象 `WeakRef` 。
