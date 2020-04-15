---
title: 实现基于C++标准库集合
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: e80ce5e7bbc6b9c6be1615dad1ea43c18e03eb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319442"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>实现基于C++标准库集合

ATL 提供`ICollectionOnSTLImpl`该接口，使您能够在对象上快速实现基于标准库的C++集合接口。 要了解此类的工作原理，您将通过一个简单的示例（下图）来使用此类来实现针对自动化客户端的只读集合。

示例代码来自[ATLCollections 示例](../overview/visual-cpp-samples.md)。

要完成此过程，您将：

- [生成新的简单对象](#vccongenerating_an_object)。

- 编辑生成的接口的[IDL 文件](#vcconedit_the_idl)。

- [创建五个类型def，](#vcconstorage_and_exposure_typedefs)描述集合项的存储方式，以及如何通过 COM 接口向客户端公开它们。

- [为复制策略类创建两个类型def。](#vcconcopy_classes)

- [为枚举器和集合实现创建类型定义](#vcconenumeration_and_collection)。

- [编辑向导生成的C++代码以使用集合类型def。](#vcconedit_the_generated_code)

- [添加代码以填充集合](#vcconpopulate_the_collection)。

## <a name="generating-a-new-simple-object"></a><a name="vccongenerating_an_object"></a>生成新的简单对象

创建新项目，确保清除"应用程序设置下的属性"框。 使用 ATL 添加类对话框和添加简单对象向导生成名为`Words`的简单对象。 确保生成调用`IWords`的双接口。 生成的类的对象将用于表示单词集合（即字符串）。

## <a name="editing-the-idl-file"></a><a name="vcconedit_the_idl"></a>编辑 IDL 文件

现在，打开 IDL 文件并添加转换为`IWords`只读集合接口所需的三个属性，如下所示：

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

这是专为使用自动化客户端设计的只读集合接口的标准表单。 此接口定义中的编号注释对应于以下注释：

1. 集合接口通常是双，因为自动化客户端通过`_NewEnum``IDispatch::Invoke`访问属性。 但是，自动化客户端可以通过 vtable 访问剩余的方法，因此双接口比接口更可取。

1. 如果双接口或 dispinterface 不会在运行时扩展（也就是说，您不会通过`IDispatch::Invoke`）提供额外的方法或属性，则应将**无邻**属性应用于定义。 此属性使自动化客户端能够在编译时执行完整的代码验证。 在这种情况下，不应扩展接口。

1. 如果希望自动化客户端能够使用此属性，则正确的 DISPID 非常重要。 （请注意，DISPID_NEWENUM中只有一个下划线。

1. 您可以提供任何值作为`Item`属性的 DISPID。 但是，`Item`通常使用DISPID_VALUE使其成为集合的默认属性。 这允许自动化客户端引用该属性而不显式命名它。

1. 就 COM 客户端而言，用于`Item`属性返回值的数据类型是存储在集合中的项的类型。 接口返回字符串，因此应使用标准 COM 字符串类型 BSTR。 您可以在内部以不同格式存储数据，稍后您将看到。

1. 用于`Count`属性的 DISPID 的值是完全任意的。 此属性没有标准 DISPID。

## <a name="creating-typedefs-for-storage-and-exposure"></a><a name="vcconstorage_and_exposure_typedefs"></a>为存储和曝光创建类型定义

定义集合接口后，您需要决定如何存储数据，以及如何通过枚举器公开数据。

这些问题的解答可以以多个 typedef 的形式提供，您可以在新创建的类的标头文件顶部附近添加：

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

在这种情况下，您将将数据存储为**std：：vector**的**std：：string**s。 **std：：vector**是一个C++标准库容器类，它类似于托管数组。 **std：：字符串**是C++标准库的字符串类。 这些类便于处理字符串集合。

由于 Visual Basic 支持对于此接口的成功至关重要，因此属性返回的`_NewEnum`枚举器必须支持`IEnumVARIANT`该接口。 这是 Visual Basic 理解的唯一枚举器接口。

## <a name="creating-typedefs-for-copy-policy-classes"></a><a name="vcconcopy_classes"></a>为复制策略类创建类型定义

到目前为止，您创建的 typedef 提供了为枚举器和集合将使用的复制类创建进一步类型定义所需的所有信息：

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

在此示例中，可以使用 VCUE_Copy.h 和`GenericCopy`VCUE_CopyString.h 中从[ATLCollections](../overview/visual-cpp-samples.md)示例中定义的自定义类。 可以在其他代码中使用此类，但可能需要定义 进`GenericCopy`一步的专门化以支持在您自己的集合中使用的数据类型。 有关详细信息，请参阅[ATL 复制策略类](../atl/atl-copy-policy-classes.md)。

## <a name="creating-typedefs-for-enumeration-and-collection"></a><a name="vcconenumeration_and_collection"></a>为枚举和收集创建类型定义

现在，以 typedefs 的形式提供了`CComEnumOnSTL`专门`ICollectionOnSTLImpl`化 和 类所需的所有模板参数。 为了简化专业化化的使用，请再创建两个类型定义，如下所示：

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

现在`CollectionType`是实现前面定义的`ICollectionOnSTLImpl``IWords`接口并提供支持`IEnumVARIANT`的枚举器的专门化的同义词。

## <a name="editing-the-wizard-generated-code"></a><a name="vcconedit_the_generated_code"></a>编辑向导生成的代码

现在，必须派生`CWords`自类型def 表示的`CollectionType`接口实现，而不是`IWords`如下所示：

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

## <a name="adding-code-to-populate-the-collection"></a><a name="vcconpopulate_the_collection"></a>添加代码以填充集合

剩下的唯一一件事是用数据填充矢量。 在这个简单示例中，您可以向类的构造函数中的集合添加几个单词：

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

现在，您可以使用您选择的客户端测试代码。

## <a name="see-also"></a>另请参阅

[集合和枚举数](../atl/atl-collections-and-enumerators.md)<br/>
[ATL集合示例](../overview/visual-cpp-samples.md)<br/>
[ATL 复制策略类](../atl/atl-copy-policy-classes.md)
