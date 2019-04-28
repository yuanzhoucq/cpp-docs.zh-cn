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
ms.openlocfilehash: 9616fcffac0b92d5ac6d96cfe5f4119f3a3b180f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223048"
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
|[WeakRef::~WeakRef 析构函数](#tilde-weakref)|取消初始化的当前实例`WeakRef`类。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[WeakRef::As 方法](#as)|设置指定`ComPtr`指针参数以表示指定的接口。|
|[WeakRef::AsIID 方法](#asiid)|设置指定`ComPtr`指针参数以表示指定的接口 id。|
|[WeakRef::CopyTo 方法](#copyto)|如果可用，请为指定的指针变量分配一个指向接口的指针。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[WeakRef::operator& 运算符](#operator-ampersand-operator)|返回`ComPtrRef`对象，表示当前`WeakRef`对象。|

## <a name="remarks"></a>备注

一个`WeakRef`对象维护*强引用*，这是与对象相关联，可以是有效或无效。 调用`As()`或`AsIID()`方法来获取强引用。 如果强引用有效，就可以访问关联的对象。 如果强引用无效 (`nullptr`)，不可访问关联的对象。

一个`WeakRef`对象通常用于表示由外部线程或应用程序控制其存在性的对象。 例如，构造`WeakRef`中对文件对象的引用的对象。 文件打开时，强引用有效。 但文件关闭时，强引用无效。

请注意，Windows 10 SDK 中的 [As](#as)、 [AsIID](#asiid) 和 [CopyTo](#copyto) 方法中没有发生行为更改。 以前，在调用任何一种方法后，你可以检查`WeakRef`为`nullptr`以确定是否强引用已成功获得，如以下代码所示：

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

使用 Windows 10 SDK（或更高版本）时以上代码无效。 相反，应检查传入的指针`nullptr`。

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

**命名空间：** Microsoft:: wrl

## <a name="tilde-weakref"></a>WeakRef:: ~ WeakRef 析构函数

取消初始化的当前实例`WeakRef`类。

```cpp
~WeakRef();
```

## <a name="as"></a>Weakref:: As 方法

设置指定`ComPtr`指针参数以表示指定的接口。

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
此操作完成后，一个对象，表示参数*U*。

### <a name="return-value"></a>返回值

- 如果此操作成功，则为 S_OK否则，一个 HRESULT，指示的原因，操作失败，并*ptr*设置为`nullptr`。

- 如果此操作成功，但当前为 S_OK`WeakRef`已释放对象。 参数*ptr*设置为`nullptr`。

- 如果此操作成功，但当前为 S_OK`WeakRef`对象不派生自参数*U*。参数*ptr*设置为`nullptr`。

### <a name="remarks"></a>备注

如果发出错误参数*U*是`IWeakReference`，或不派生自`IInspectable`。

第一个模板是应在代码中使用的表单。 第二个模板是支持 [自动](../../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

从 Windows 10 SDK 开始，此方法不设置`WeakRef`实例向`nullptr`如果无法获得弱引用，因此应避免的错误检查代码，用于检查`WeakRef`为`nullptr`。 相反，应检查*ptr*为`nullptr`。

## <a name="asiid"></a>Weakref:: Asiid 方法

设置指定`ComPtr`指针参数以表示指定的接口 id。

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
此操作完成后，一个对象，表示参数*riid*。

### <a name="return-value"></a>返回值

- 如果此操作成功，则为 S_OK否则，一个 HRESULT，指示的原因，操作失败，并*ptr*设置为`nullptr`。

- 如果此操作成功，但当前为 S_OK`WeakRef`已释放对象。 参数*ptr*设置为`nullptr`。

- 如果此操作成功，但当前为 S_OK`WeakRef`对象不派生自参数*riid*。 参数*ptr*设置为`nullptr`。 (有关更多信息，请参阅“备注”。)

### <a name="remarks"></a>备注

如果发出错误参数*riid*不派生自`IInspectable`。 此错误将取代返回值。

第一个模板是应在代码中使用的表单。 第二个模板（此处未显示，但在头文件中声明）是支持 [自动](../../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

从 Windows 10 SDK 开始，此方法不设置`WeakRef`实例向`nullptr`如果无法获得弱引用，因此应避免的错误检查代码，用于检查`WeakRef`为`nullptr`。 相反，应检查*ptr*为`nullptr`。

## <a name="copyto"></a>Weakref:: Copyto 方法

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
指针`IInspectable`接口。 如果错误发出*U*不派生自`IInspectable`。

*riid*<br/>
接口 ID。 如果错误发出*riid*不派生自`IWeakReference`。

*ptr*<br/>
指向的双向间接指针`IInspectable`或`IWeakReference`。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。 有关更多信息，请参见**备注**。

### <a name="remarks"></a>备注

返回值 S_OK 表示此操作成功，但并不指示弱引用是否解析为强引用。 如果返回 S_OK，则测试参数*p*是否为强引用; 即，参数*p*不等于`nullptr`。

从 Windows 10 SDK 开始，此方法不设置`WeakRef`实例向`nullptr`如果无法获得弱引用，因此应避免的错误检查代码，用于检查`WeakRef`为`nullptr`。 相反，应检查*ptr*为`nullptr`。

## <a name="operator-ampersand-operator"></a>Weakref::&amp;运算符

返回`ComPtrRef`对象，表示当前`WeakRef`对象。

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>返回值

一个`ComPtrRef`对象，表示当前`WeakRef`对象。

### <a name="remarks"></a>备注

这是不是要在代码中使用的内部帮助器运算符。

## <a name="weakref"></a>Weakref:: Weakref 构造函数

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
指针、 引用或对现有对象的初始化当前的右值引用`WeakRef`对象。

### <a name="remarks"></a>备注

第一个构造函数会初始化一个空`WeakRef`对象。 第二个构造函数初始化`WeakRef`从指向的对象`IWeakReference`接口。 第三个构造函数初始化`WeakRef`对象的引用从`ComPtr<IWeakReference>`对象。 第四个和第五个构造函数初始化`WeakRef`从另一个对象`WeakRef`对象。
