---
title: Platform::Collections 命名空间
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
ms.openlocfilehash: ab6b78f1b88c586a11276d36387fb42ea6ee667f
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032416"
---
# <a name="platformcollections-namespace"></a>Platform::Collections 命名空间

平台：：集合命名空间包含`Map`、`MapView`和`Vector``VectorView`类。 这些类是在 [Windows::Foundation::Collections](/uwp/api/windows.foundation.collections) 命名空间中定义的对应接口的具体实现。 具体集合类型在 ABI 之间是不可移植的（例如，当 Javascript 或 C# 程序调用到 C++ 组件时）时，但它们可以隐式转换为其相应的接口类型。 例如，如果你实现了一个填充并返回集合的公共方法，则使用 [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) 在内部实现该集合并使用 [Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1) 作为返回类型。 有关详细信息，请参阅C++ 中的["集合](../cppcx/collections-c-cx.md)"和["创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)"。

可以从 [std::vector](../standard-library/vector-class.md) 构造 Platform::Collections::Vector，从 [std::map](../cppcx/platform-collections-map-class.md) 构造 [Platform::Collections::Map](../standard-library/map-class.md)。

此外，平台：集合命名空间支持回插入和输入迭代器以及`Vector`迭代`VectorView`器。

您必须包括 （`#include`） 集合.h 标头才能在平台：：集合命名空间中使用类型。

## <a name="syntax"></a>语法

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>成员

此命名空间包含以下成员。

|名称|说明|
|----------|-----------------|
|[Platform::Collections::BackInsertIterator 类](../cppcx/platform-collections-backinsertiterator-class.md)|表示在集合末尾插入一个元素的迭代器。|
|[平台：集合：：输入迭代器类](../cppcx/platform-collections-inputiterator-class.md)|表示在集合开头插入一个元素的迭代器。|
|[Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)|表示键访问的键值对的可修改集合。 类似于 [std::map](../standard-library/map-class.md)。|
|[平台：：集合：MapView 类](../cppcx/platform-collections-mapview-class.md)|表示键访问的键值对的只读集合。|
|[平台：集合：：矢量类](../cppcx/platform-collections-vector-class.md)|表示元素的可修改序列。 类似于 [std::vector](../standard-library/vector-class.md)。|
|[平台：集合：：矢量迭代器类](../cppcx/platform-collections-vectoriterator-class.md)|表示遍历 `Vector` 集合的迭代器。|
|[平台：：集合：：矢量视图类](../cppcx/platform-collections-vectorview-class.md)|表示元素的只读序列。|
|[Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)|表示遍历 `VectorView` 集合的迭代器。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>要求

**元数据：** 平台.winmd

**命名空间：** Platform::Collections

**编译器选项：** /ZW

## <a name="see-also"></a>请参阅

[平台命名空间](../cppcx/platform-namespace-c-cx.md)
