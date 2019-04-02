---
title: 如何：创建类型安全集合
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
ms.openlocfilehash: c8be781bad699edb8cb0be844d79802269c3e0c5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781518"
---
# <a name="how-to-make-a-type-safe-collection"></a>如何：创建类型安全集合

本文介绍如何针对您自己的数据类型生成类型安全的集合。 包括以下主题：

- [使用基于模板的类的类型安全性，](#_core_using_template.2d.based_classes_for_type_safety)

- [实现帮助器函数](#_core_implementing_helper_functions)

- [使用非模板集合类](#_core_using_nontemplate_collection_classes)

Microsoft 基础类库提供基于 C++ 模板的预定义类型安全集合。 由于它们是模板，因此这些类帮助提供类型安全并且易于使用，不必进行类型转换和其他与为了此目的使用非模板类有关的额外的工作。 MFC 示例[收集](../overview/visual-cpp-samples.md)演示如何使用 MFC 应用程序中的基于模板的集合类。 一般将在编写新集合代码时使用这些类。

##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> 为了类型安全使用基于模板的类

#### <a name="to-use-template-based-classes"></a>使用基于模板的类

1. 声明集合类类型的变量。 例如：

   [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. 调用集合对象的成员函数。 例如：

   [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. 如有必要，实现[帮助器函数](../mfc/reference/collection-class-helpers.md)并[SerializeElements](../mfc/reference/collection-class-helpers.md#serializeelements)。 有关实现这些函数的信息，请参阅[实现帮助器函数](#_core_implementing_helper_functions)。

此示例演示对整数列表的声明。 步骤 1 中的第一个参数是作为列表的元素存储的数据的类型。 第二个参数指定传递到和从成员函数的集合类，如返回数据的方式`Add`和`GetAt`。

##  <a name="_core_implementing_helper_functions"></a> 实现帮助器函数

基于模板的集合类 `CArray`、`CList` 和 `CMap` 使用您可根据需要为派生集合类自定义的 5 个全局帮助器函数。 有关这些帮助器函数的信息，请参阅[集合类帮助器](../mfc/reference/collection-class-helpers.md)中*MFC 参考*。 基于模板的集合类的大部分使用需要实现序列化函数。

###  <a name="_core_serializing_elements"></a> 序列化元素

`CArray`、`CList` 和 `CMap` 类将调用 `SerializeElements` 以将集合元素存储到存档中或从存档中读取集合元素。

`SerializeElements` 帮助器函数的默认实现将执行从对象到存档的位写入，或从存档到对象的位读取，具体取决于是将对象存储在存档中还是从存档中检索对象。 如果此操作不合适，则请重写 `SerializeElements`。

如果您的集合存储派生自 `CObject` 的对象并且您在集合元素类的实现中使用 `IMPLEMENT_SERIAL` 宏，则可以使用内置于 `CArchive` 和 `CObject` 的序列化功能：

[!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

重载的插入运算符`CArchive`调用`CObject::Serialize`（或该函数的重写） 为每个`CPerson`对象。

##  <a name="_core_using_nontemplate_collection_classes"></a> 使用非模板集合类

MFC 还支持 MFC 1.0 版引入的集合类。 这些类都不基于模板。 它们可用于包含受支持的类型的数据`CObject*`， `UINT`， `DWORD`，和`CString`。 您可以使用这些预定义的集合（如 `CObList`）保存派生自 `CObject` 的任何对象的集合。 MFC 还提供了其他预定义的集合以保存基元类型，如`UINT`和 void 指针 (`void`*)。 但一般来说，定义自己的类型安全集合来保存更特定的类的对象及其派生类型往往很有用。 请注意，使用不基于模板的集合类这样做比使用基于模板的类工作量大。

使用非模板集合创建类型安全的集合有两种方式：

1. 如有必要，将非模板集合与类型转换一起使用。 这是更简单的方法。

1. 从非模板类型安全集合派生和扩展非模板类型安全集合。

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>将非模板集合与类型转换一起使用

1. 直接使用非模板类之一（如 `CWordArray`）。

   例如，您可以创建一个 `CWordArray` 并为其添加任何 32 位值，然后检索这些值。 再无任何操作。 只需使用预定义函数。

   您也可以使用预定义集合（如 `CObList`）保存派生自 `CObject` 的任何对象。 将定义 `CObList` 集合以保存指向 `CObject` 的指针。 从列表中检索对象时，您可能必须将结果转换为适当的类型，因为 `CObList` 函数将返回指向 `CObject` 的指针。 例如，如果您将 `CPerson` 对象存储在 `CObList` 集合中，则必须将检索的元素转换为指向 `CPerson` 对象的指针。 以下示例使用 `CObList` 集合保存 `CPerson` 对象：

   [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   使用预定义集合类型和根据需要进行转换的方法可能满足您集合的许多需求。 如果您需要更多函数或更多类型安全，请使用基于模板的类或执行下面的过程。

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>派生和扩展非模板类型安全的集合

1. 从预定义的非模板类派生您自己的集合类。

   派生类时，您可以添加类型安全的包装器函数以为现有函数提供一个类型安全的接口。

   例如，如果要从 `CObList` 派生一个列表来保存 `CPerson` 对象，则您可能添加包装器函数 `AddHeadPerson` 和 `GetHeadPerson`，如下所示。

   [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   这些包装器函数为从派生列表添加和检索 `CPerson` 对象提供了一种类型安全的方法。 您可以看到，对于 `GetHeadPerson` 函数，您将封装类型转换。

   您还可通过定义扩展集合功能的新函数而不是将现有函数包装在类型安全的包装器中来添加新函数。 例如，文章[删除 CObject 集合中的所有对象](../mfc/deleting-all-objects-in-a-cobject-collection.md)描述函数用于删除列表中包含的所有对象。 此函数无法作为成员函数添加到派生类中。

## <a name="see-also"></a>请参阅

[集合](../mfc/collections.md)
