---
title: WeakReference 类
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: a80c0ec14da2a955a95ac84dd3975212ef20ae04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374216"
---
# <a name="weakreference-class"></a>WeakReference 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
class WeakReference;
```

## <a name="remarks"></a>备注

表示可与 Windows 运行时或经典 COM 一起使用*的弱引用*。 弱引用表示可能可访问或可能不可访问的对象。

对象维护*强引用*，它是指向对象的指针和*强引用计数*，即该方法`Resolve()`分发的强引用的副本数。 `WeakReference` 虽然强引用计数是非零的，但强引用是有效的，并且对象是可访问的。 当强引用计数变为零时，强引用无效，并且对象不可访问。

对象`WeakReference`通常用于表示其存在由外部线程或应用程序控制的对象。 例如，从对文件`WeakReference`对象的引用构造对象。 文件打开时，强引用有效。 但文件关闭时，强引用无效。

这些方法`WeakReference`是线程安全的。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                  | 说明
----------------------------------------------------- | ---------------------------------------------------------------------------
[弱参考：：弱参考](#weakreference)        | 初始化 `WeakReference` 类的新实例。
[弱参考：*弱参考](#tilde-weakreference) | 取消初始化（销毁）`WeakReference`类的当前实例。

### <a name="public-methods"></a>公共方法

名称                                                                 | 说明
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[弱参考：:D强参考](#decrementstrongreference) | 声明当前`WeakReference`对象的强引用计数。
[弱参考：：增量强参考](#incrementstrongreference) | 增加当前`WeakReference`对象的强引用计数。
[弱参考：：解决](#resolve)                                   | 如果强引用计数为非零，则设置指向当前强引用值的指定指针。
[弱参考：：设置未知](#setunknown)                             | 将当前`WeakReference`对象的强引用设置到指定的接口指针。

## <a name="inheritance-hierarchy"></a>继承层次结构

`WeakReference`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** 微软：：WRL：:D

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>弱参考：*弱参考

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

取消初始化类的`WeakReference`当前实例。

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>弱参考：:D强参考

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>备注

声明当前`WeakReference`对象的强引用计数。

当强引用计数变为零时，强引用设置为`nullptr`。

### <a name="return-value"></a>返回值

递减的强引用计数。

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>弱参考：：增量强参考

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>返回值

递增的强引用计数。

### <a name="remarks"></a>备注

增加当前`WeakReference`对象的强引用计数。

## <a name="weakreferenceresolve"></a><a name="resolve"></a>弱参考：：解决

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*ppvObject*<br/>
此操作完成后，如果强引用计数为非零，则当前强引用的副本。

### <a name="return-value"></a>返回值

- 如果此操作成功且强引用计数为零，S_OK。 *ppvObject*参数设置为`nullptr`。

- 如果此操作成功且强引用计数为非零，则S_OK。 *ppvObject*参数设置为强引用。

- 否则，指示此操作失败原因的 HRESULT。

### <a name="remarks"></a>备注

如果强引用计数为非零，则设置指向当前强引用值的指定指针。

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>弱参考：：设置未知

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>参数

*unk*<br/>
指向对象`IUnknown`接口的指针。

### <a name="remarks"></a>备注

将当前`WeakReference`对象的强引用设置到指定的接口指针。

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>弱参考：：弱参考

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
WeakReference();
```

### <a name="remarks"></a>备注

初始化 `WeakReference` 类的新实例。

`WeakReference`对象的强引用指针初始化到`nullptr`，强引用计数初始化为 1。
