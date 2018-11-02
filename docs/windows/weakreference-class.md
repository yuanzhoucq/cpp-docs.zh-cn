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
ms.openlocfilehash: a3372a176a158dd9c89eb888c8deb0244eef9a84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654930"
---
# <a name="weakreference-class"></a>WeakReference 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
class WeakReference;
```

## <a name="remarks"></a>备注

表示*弱引用*可以用于 Windows 运行时或经典 com。 弱引用表示可能可访问或可能不可访问的对象。

一个`WeakReference`对象维护*强引用*，这是指向对象的指针和一个*强引用计数*，这是已通过分发的强引用的副本数`Resolve()`方法。 非零值的强引用计数时，强引用有效且该对象是可访问。 当强引用计数变为零时，强引用无效，该对象是不可访问。

一个`WeakReference`对象通常用于表示由外部线程或应用程序控制其存在性的对象。 例如，构造`WeakReference`中对文件对象的引用的对象。 文件打开时，强引用有效。 但文件关闭时，强引用无效。

`WeakReference`是线程安全的方法。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                  | 描述
----------------------------------------------------- | ---------------------------------------------------------------------------
[Weakreference:: Weakreference](#weakreference)        | 初始化 `WeakReference` 类的新实例。
[WeakReference:: ~ WeakReference](#tilde-weakreference) | 取消初始化 （销毁） 的当前实例`WeakReference`类。

### <a name="public-methods"></a>公共方法

名称                                                                 | 描述
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[Weakreference:: Decrementstrongreference](#decrementstrongreference) | 强引用计数当前`WeakReference`对象。
[Weakreference:: Incrementstrongreference](#incrementstrongreference) | 当前的强引用计数递增`WeakReference`对象。
[WeakReference::Resolve](#resolve)                                   | 将指定的指针设置为当前的强引用值，如果强引用计数不为零。
[Weakreference:: Setunknown](#setunknown)                             | 设置当前的强引用`WeakReference`对象与指定的接口指针。

## <a name="inheritance-hierarchy"></a>继承层次结构

`WeakReference`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="tilde-weakreference"></a>WeakReference:: ~ WeakReference

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

取消初始化的当前实例`WeakReference`类。

## <a name="decrementstrongreference"></a>Weakreference:: Decrementstrongreference

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>备注

强引用计数当前`WeakReference`对象。

当强引用计数变为零时，强引用设置为`nullptr`。

### <a name="return-value"></a>返回值

递减的强引用计数。

## <a name="incrementstrongreference"></a>Weakreference:: Incrementstrongreference

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>返回值

递增的强引用计数。

### <a name="remarks"></a>备注

当前的强引用计数递增`WeakReference`对象。

## <a name="resolve"></a>Weakreference:: Resolve

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
此操作完成后，当前的强引用，如果强引用计数不为零的副本。

### <a name="return-value"></a>返回值

- 如果此操作是成功的强引用计数为零，则为 S_OK。 *PpvObject*参数设置为`nullptr`。

- 如果此操作成功，则为 S_OK 和强引用计数为非零值。 *PpvObject*参数设置为强引用。

- 否则，一个 HRESULT，指示的原因，此操作失败。

### <a name="remarks"></a>备注

将指定的指针设置为当前的强引用值，如果强引用计数不为零。

## <a name="setunknown"></a>Weakreference:: Setunknown

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>参数

*unk*<br/>
一个指向`IUnknown`接口的对象。

### <a name="remarks"></a>备注

设置当前的强引用`WeakReference`对象与指定的接口指针。

## <a name="weakreference"></a>Weakreference:: Weakreference

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
WeakReference();
```

### <a name="remarks"></a>备注

初始化 `WeakReference` 类的新实例。

中的强引用指针`WeakReference`对象初始化为`nullptr`，并且强引用计数初始化为 1。
