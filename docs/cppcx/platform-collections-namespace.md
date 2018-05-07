---
title: 'Platform:: collections Namespace |Microsoft 文档'
ms.custom: ''
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
dev_langs:
- C++
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b4e38d6a051481b2b5f642c6b4de3c837f8fbfd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="platformcollections-namespace"></a>Platform::Collections 命名空间

Platform:: collections 命名空间包含`Map`， `MapView`， `Vector`，和`VectorView`类。 这些类是在 [Windows::Foundation::Collections](http://go.microsoft.com/fwlink/p/?LinkId=262645) 命名空间中定义的对应接口的具体实现。 具体集合类型在 ABI 之间是不可移植的（例如，当 Javascript 或 C# 程序调用到 C++ 组件时）时，但它们可以隐式转换为其相应的接口类型。 例如，如果你实现了一个填充并返回集合的公共方法，则使用 [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) 在内部实现该集合并使用 [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) 作为返回类型。 有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)和[创建 Windows 运行时 c + + 组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

可以从 [std::vector](../standard-library/vector-class.md) 构造 Platform::Collections::Vector，从 [std::map](../cppcx/platform-collections-map-class.md) 构造 [Platform::Collections::Map](../standard-library/map-class.md)。

此外，platform:: collections 命名空间提供对于回插和输入迭代器和`Vector`和`VectorView`迭代器。

必须包括 (`#include`) collection.h 标头才能使用 platform:: collections 命名空间中的类型。

## <a name="syntax"></a>语法

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>成员

此命名空间包含以下成员。

|名称|描述|
|----------|-----------------|
|[Platform::Collections::BackInsertIterator 类](../cppcx/platform-collections-backinsertiterator-class.md)|表示在集合末尾插入一个元素的迭代器。|
|[Platform::Collections::InputIterator 类](../cppcx/platform-collections-inputiterator-class.md)|表示在集合开头插入一个元素的迭代器。|
|[Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)|表示键访问的键值对的可修改集合。 类似于 [std::map](../standard-library/map-class.md)。|
|[Platform::Collections::MapView 类](../cppcx/platform-collections-mapview-class.md)|表示键访问的键值对的只读集合。|
|[Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)|表示元素的可修改序列。 类似于 [std::vector](../standard-library/vector-class.md)。|
|[Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)|表示遍历 `Vector` 集合的迭代器。|
|[Platform::Collections::VectorView 类](../cppcx/platform-collections-vectorview-class.md)|表示元素的只读序列。|
|[Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)|表示遍历 `VectorView` 集合的迭代器。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[平台命名空间](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>要求

**元数据：** platform.winmd

**命名空间：** Platform::Collections

**编译器选项：** /ZW

## <a name="see-also"></a>请参阅

[平台 Namespace](../cppcx/platform-namespace-c-cx.md)  
