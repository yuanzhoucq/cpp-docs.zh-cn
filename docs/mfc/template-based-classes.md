---
title: 基于模板的类
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
ms.openlocfilehash: 29f5f815b62835aedbca1f79b797f826ea53d83b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370458"
---
# <a name="template-based-classes"></a>基于模板的类

本文在 MFC 版本 3.0 及更高版本中介绍了基于类型安全模板的集合类。 使用这些模板创建类型安全集合比使用不基于模板的集合类更方便，并有助于更有效地提供类型安全性。

MFC 预定义了两类基于模板的集合：

- [简单的数组、列表和地图类](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [类型指针的数组、列表和映射](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

简单集合类都派生自类`CObject`，因此它们继承了 的`CObject`序列化、动态创建和其他属性。 类型化的指针集合类要求您指定派生自的类 — 它必须是 MFC 预定义的非模板指针集合之一，例如`CPtrList`或`CPtrArray`。 新的集合类从指定的基类继承，而新类的成员函数使用对基类成员的封装调用来强制实施类型安全。

有关C++模板的详细信息，请参阅*C++语言参考*中的[模板](../cpp/templates-cpp.md)。

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>使用简单数组、列表和地图模板

要使用简单的收集模板，您需要了解可以在这些集合中存储哪些类型的数据，以及集合声明中要使用的参数。

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>简单的数组和列表用法

简单的数组和列表类[CArray](../mfc/reference/carray-class.md)和[CList](../mfc/reference/clist-class.md)采用两个参数 *：TYPE*和`ARG_TYPE`。 这些类可以存储您在*TYPE*参数中指定的任何数据类型：

- 基本C++数据类型，如**int**、**字符**和**浮点**

- C++结构和类

- 您定义的其他类型

为方便和效率，可以使用*ARG_TYPE*参数指定函数参数的类型。 通常，ARG_TYPE指定*为*对*TYPE*参数中命名类型的引用。 例如：

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

第一个示例声明包含`myArray`**int**s 的数组集合 。 第二个示例声明存储`myList``CPerson`对象的列表集合 。 集合类的某些成员函数采用其类型由*ARG_TYPE*模板参数指定的参数。 例如，`Add`类`CArray`的成员函数采用*ARG_TYPE*参数：

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>简单的地图使用

简单的地图类[CMap](../mfc/reference/cmap-class.md)采用四个参数：*键**、ARG_KEY、VALUE*和*ARG_VALUE*。 *VALUE* 与数组和列表类一样，地图类可以存储任何数据类型。 与数组和列表（哪个数组和列表）（它们存储的数据编制索引和排序）不同，映射关联键和值：通过指定值的关联键来访问存储在地图中的值。 *KEY*参数指定用于访问存储在地图中的数据的键的数据类型。 如果*KEY*的类型是结构或类，*则ARG_KEY*参数通常是对*KEY*中指定的类型的引用。 *VALUE*参数指定存储在地图中的项的类型。 如果*ARG_VALUE*的类型是结构或类，*则ARG_VALUE*参数通常是对*VALUE*中指定的类型的引用。 例如：

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

第一个示例`MY_STRUCT`存储值，通过**int**键访问值，并通过引用`MY_STRUCT`返回访问的项目。 第二个示例`CPerson`存储值，按`CString`键访问值，并返回对已访问项的引用。 此示例可能表示一个简单的通讯簿，您可以在其中按姓氏查找人员。

由于*KEY*参数`CString`的类型和*KEY_TYPE*`LPCSTR`参数的类型，因此键作为类型的`CString`项存储在地图中，但在函数中引用，例如`SetAt`通过类型的`LPCSTR`指针。 例如：

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>使用键入指针收集模板

要使用类型化指针集合模板，您需要了解可以在这些集合中存储哪些类型的数据，以及集合声明中要使用的参数。

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>键入指针数组和列表使用情况

类型指针数组和列表类[CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)和[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)采用两个参数 *：BASE_CLASS*和*TYPE*。 这些类可以存储您在*TYPE*参数中指定的任何数据类型。 它们派生自存储指针的非模板集合类之一;在*BASE_CLASS*中指定此基类。 对于数组，请使用 或`CObArray``CPtrArray`。 对于列表，请使用`CObList`或`CPtrList`。

实际上，当您基于，例如`CObList`，宣布集合时，新类不仅继承其基类的成员，而且还声明许多额外的类型安全成员函数和运算符，这些函数和运算符通过封装对基类成员的调用来帮助提供类型安全性。 这些封装管理所有必要的类型转换。 例如：

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

第一个示例声明类型指针数组派生`myArray`自`CObArray`。 数组存储并返回指向`CPerson`对象的指针（其中`CPerson`是从 派生的`CObject`类）。 您可以`CObArray`调用任何成员函数，也可以调用新的类型`GetAt`安全函数`ElementAt`或使用类型安全 ***运算符**。

第二个示例声明从`myList``CPtrList`派生的键入的指针列表。 该列表存储并返回指向`MY_STRUCT`对象的指针。 基于 的`CPtrList`类用于存储指向未派生自`CObject`的对象的指针。 `CTypedPtrList`具有许多类型`GetHead`安全成员函数： 、 `GetTail`、 `RemoveHead`、 `RemoveTail` `GetNext`、 `GetPrev`、`GetAt`和 。

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>键入指针映射使用情况

类型指针映射类[CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)采用三个参数 *：BASE_CLASS、**键*和*VALUE*。 *BASE_CLASS*参数指定从中派生新类`CMapPtrToWord`的类： 、 `CMapPtrToPtr`、 `CMapStringToPtr`、 `CMapWordToPtr` `CMapStringToOb`、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 *KEY*与 中的*KEY*`CMap`KEY 类似：它指定用于查找的密钥的类型。 *VALUE*类似于 中的`CMap` *VALUE，* 它指定存储在地图中的对象类型。 例如：

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

第一个示例是基于`CMapPtrToPtr`的映射 ，`CString`它使用映射到 指向`MY_STRUCT`的指针的键。 您可以通过调用类型安全`Lookup`成员函数来查找存储的指针。 您可以使用 ***运算符**查找存储的指针，如果找不到，则添加它。 您可以使用类型安全`GetNextAssoc`函数迭代地图。 您还可以调用类`CMapPtrToPtr`的其他成员函数。

第二个示例是基于`CMapStringToOb`的映射 ， 它使用映射到存储到`CMyObject`对象的指针的字符串键。 您可以使用上一段中描述的相同类型安全成员，也可以调用类`CMapStringToOb`的成员 。

> [!NOTE]
> 如果为*VALUE*参数指定**类**或**结构**类型，而不是指向该类型的指针或引用，则类或结构必须具有复制构造函数。

有关详细信息，请参阅[如何创建类型安全集合](../mfc/how-to-make-a-type-safe-collection.md)。

## <a name="see-also"></a>另请参阅

[集合](../mfc/collections.md)
