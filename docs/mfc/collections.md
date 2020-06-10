---
title: 集合
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, collections
- arrays [MFC], classes
- MFC collection classes
- shapes, collection
- collection classes [MFC], MFC
- collections, about collections
- array templates [MFC]
- collection classes [MFC], template-based
- collection classes [MFC], about collection classes
- collection classes [MFC], maps
- collection classes [MFC], arrays
- shapes
- collection classes [MFC], lists
- collection classes [MFC], shapes
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
ms.openlocfilehash: f2cd03afbb09dff38298454658c3d3dc2dfa6a8a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619352"
---
# <a name="collections"></a>集合

Microsoft 基础类库提供了用来管理对象的组的集合类。 这些类有两种类型：

- [从 C++ 模板创建的集合类](#_core_the_template_based_collection_classes)

- [并非从模板创建的集合类](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> 如果代码已使用非模板集合类，你可以继续使用它们。 如果您为自己的数据类型编写了新的类型安全集合类，则建议使用较新的基于模板的类。

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a>集合形状

集合类以其“形式”和元素类型为特征。 形式指的是集合组织和存储对象的方式。 MFC 提供了三个基本集合形式：列表、数组和映射（也称为字典）。 你可以选取最适合你的特定编程问题的集合形式。

本主题的后面部分简要分别介绍了所提供的三种集合形式。 若要比较形状的功能以帮助您决定哪一种最适合您的程序，请参阅[有关选择集合类的建议](recommendations-for-choosing-a-collection-class.md)。

- 列表

   列表类提供了元素的有序非索引列表，该列表作为双向链接列表实现。 列表具有“头”和“尾”，它在头和尾中添加/移除元素或在中间插入/删除元素非常快。

- Array

   数组类提供了一个以动态方式调整大小、经过排序且编制了整数索引的对象数组。

- 映射（也称为字典）

   映射是将键对象与值对象关联的集合。

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a>基于模板的集合类

若要实现包含任何类型的对象的类型安全的集合，最简单的方法是使用其中一个基于 MFC 模板的类。 有关这些类的示例，请参阅 MFC 示例[收集](../overview/visual-cpp-samples.md)。

下表列出了基于 MFC 模板的集合类。

### <a name="collection-template-classes"></a>集合模板类

|集合内容|数组|列表|Maps|
|-------------------------|------------|-----------|----------|
|任何类型的对象的集合|`CArray`|`CList`|`CMap`|
|指向任何类型的对象的指针的集合|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a>不基于模板的集合类

如果应用程序已使用 MFC 非模板类，则可以继续使用它们。 但是，对于新集合，建议使用基于模板的类。 下表列出了不基于模板的 MFC 集合类。

### <a name="nontemplate-collection-classes"></a>非模板集合类

|数组|列表|Maps|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

[有关选择集合类的建议](recommendations-for-choosing-a-collection-class.md)中的 Mfc 集合类表的特征介绍了 mfc 集合类的以下特征：

- 类是否使用 C++ 模板

- 存储在集合中的元素是否可以序列化

- 存储在集合中的元素是否可以转储以供诊断

- 集合是否为类型安全的

### <a name="what-do-you-want-to-do"></a>要执行的操作

#### <a name="general-collection-class-tasks"></a>常规集合类任务

- [选择集合类的建议](recommendations-for-choosing-a-collection-class.md)

- [如何：创建类型安全集合](how-to-make-a-type-safe-collection.md)

- [创建堆栈和队列集合](creating-stack-and-queue-collections.md)

- [CArray：： Add](reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>基于模板的集合类任务

- [基于模板的类](template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>访问集合（基于或不基于模板）的成员

- [访问集合的所有成员](accessing-all-members-of-a-collection.md)

- [正在删除 CObject 集合中的所有对象](deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>另请参阅

[概念](mfc-concepts.md)<br/>
[常规 MFC 主题](general-mfc-topics.md)
