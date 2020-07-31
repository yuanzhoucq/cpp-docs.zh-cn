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
ms.openlocfilehash: 9a367a61a029abe1be599b1e262e279402149ccd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220452"
---
# <a name="weakreference-class"></a>WeakReference 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
class WeakReference;
```

## <a name="remarks"></a>备注

表示可与 Windows 运行时或经典 COM 一起使用的*弱引用*。 弱引用表示可能可访问或可能不可访问的对象。

`WeakReference`对象维护*强引用*，这是一个指向对象的指针和一个*强引用计数*，它是由方法分发的强引用的副本数 `Resolve()` 。 如果强引用计数为非零，则强引用有效并且对象可访问。 当强引用计数变为零时，强引用将无效，并且对象不可访问。

`WeakReference`对象通常用于表示由外部线程或应用程序控制其存在性的对象。 例如， `WeakReference` 通过对文件对象的引用构造对象。 文件打开时，强引用有效。 但文件关闭时，强引用无效。

`WeakReference`方法是线程安全的。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                  | 描述
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference：： WeakReference](#weakreference)        | 初始化 `WeakReference` 类的新实例。
[WeakReference：： ~ WeakReference](#tilde-weakreference) | 取消初始化（销毁）类的当前实例 `WeakReference` 。

### <a name="public-methods"></a>公共方法

“属性”                                                                 | 描述
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference：:D ecrementStrongReference](#decrementstrongreference) | 递减当前对象的强引用计数 `WeakReference` 。
[WeakReference：： IncrementStrongReference](#incrementstrongreference) | 递增当前对象的强引用计数 `WeakReference` 。
[WeakReference：： Resolve](#resolve)                                   | 如果强引用计数为非零，则将指定的指针设置为当前强引用值。
[WeakReference：： SetUnknown](#setunknown)                             | 将当前对象的强引用设置 `WeakReference` 为指定接口指针。

## <a name="inheritance-hierarchy"></a>继承层次结构

`WeakReference`

## <a name="requirements"></a>要求

**标头：** 实现。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>WeakReference：： ~ WeakReference

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

取消初始化类的当前实例 `WeakReference` 。

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>WeakReference：:D ecrementStrongReference

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>备注

递减当前对象的强引用计数 `WeakReference` 。

当强引用计数变为零时，强引用会设置为 **`nullptr`** 。

### <a name="return-value"></a>返回值

递减的强引用计数。

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>WeakReference：： IncrementStrongReference

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>返回值

递增的强引用计数。

### <a name="remarks"></a>备注

递增当前对象的强引用计数 `WeakReference` 。

## <a name="weakreferenceresolve"></a><a name="resolve"></a>WeakReference：： Resolve

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
完成此操作后，如果强引用计数为非零，则为当前强引用的副本。

### <a name="return-value"></a>返回值

- 如果此操作成功且强引用计数为零，则 S_OK。 *PpvObject*参数设置为 **`nullptr`** 。

- 如果此操作成功，则为 S_OK，强引用计数不为零。 *PpvObject*参数设置为强引用。

- 否则，为指示此操作失败原因的 HRESULT。

### <a name="remarks"></a>备注

如果强引用计数为非零，则将指定的指针设置为当前强引用值。

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>WeakReference：： SetUnknown

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>参数

*unk*<br/>
指向对象的接口的指针 `IUnknown` 。

### <a name="remarks"></a>备注

将当前对象的强引用设置 `WeakReference` 为指定接口指针。

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>WeakReference：： WeakReference

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
WeakReference();
```

### <a name="remarks"></a>备注

初始化 `WeakReference` 类的新实例。

对象的强引用指针 `WeakReference` 初始化为 **`nullptr`** ，强引用计数初始化为1。
