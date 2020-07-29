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
ms.openlocfilehash: eceee4421b43515b9b246f4af26a1a3741c6b25b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230449"
---
# <a name="template-based-classes"></a>基于模板的类

本文介绍 MFC 版本3.0 及更高版本中基于类型安全模板的集合类。 使用这些模板创建类型安全的集合更方便，并与不基于模板的集合类更有效地提供类型安全性。

MFC 预定义两类基于模板的集合：

- [简单数组、列表和映射类](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [类型化指针的数组、列表和映射](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

简单集合类都是从类派生的 `CObject` ，因此它们继承了的序列化、动态创建和其他属性 `CObject` 。 类型化指针集合类需要指定派生自的类，该类必须是由 MFC 预定义的非模板指针集合之一，例如 `CPtrList` 或 `CPtrArray` 。 新集合类继承自指定的基类，新类的成员函数使用对基类成员的封装调用来强制类型安全。

有关 c + + 模板的详细信息，请参阅*c + + 语言参考*中的[模板](../cpp/templates-cpp.md)。

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>使用简单数组、列表和映射模板

若要使用简单集合模板，你需要知道可以在这些集合中存储的数据类型，以及要在集合声明中使用哪些参数。

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>简单数组和列表用法

简单的数组和列表类[CArray](../mfc/reference/carray-class.md)和[CList](../mfc/reference/clist-class.md)采用两个参数：*类型*和 `ARG_TYPE` 。 这些类可以存储在*类型*参数中指定的任何数据类型：

- 基本 c + + 数据类型，如 **`int`** 、 **`char`** 和**`float`**

- C + + 结构和类

- 你定义的其他类型

为方便和提高效率，可以使用*ARG_TYPE*参数来指定函数参数的类型。 通常，将*ARG_TYPE*指定为对在*类型*参数中命名的类型的引用。 例如：

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

第一个示例声明数组集合， `myArray` 其中包含 **`int`** 。 第二个示例声明一个 `myList` 用于存储对象的列表集合 `CPerson` 。 集合类的某些成员函数接受其类型由*ARG_TYPE*模板参数指定的参数。 例如，类的 `Add` 成员函数 `CArray` 采用*ARG_TYPE*参数：

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>简单映射用法

简单地图类[CMap](../mfc/reference/cmap-class.md)采用四个参数： *KEY*、 *ARG_KEY*、 *VALUE*和*ARG_VALUE*。 与数组和列表类一样，map 类可以存储任何数据类型。 与数组和列表不同，后者对它们存储的数据进行索引和排序，map 关联键和值：通过指定值的关联键来访问存储在映射中的值。 *KEY*参数指定用于访问存储在映射中的数据的键的数据类型。 如果*键*的类型为结构或类，则*ARG_KEY*参数通常是对*键*中指定的类型的引用。 *值*参数指定存储在映射中的项的类型。 如果*ARG_VALUE*的类型为结构或类，则*ARG_VALUE*参数通常是对*值*中指定的类型的引用。 例如：

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

第一个示例存储 `MY_STRUCT` 值，按密钥访问这些值， **`int`** 并 `MY_STRUCT` 按引用返回访问的项目。 第二个示例存储 `CPerson` 值，按键访问这些值， `CString` 并返回对访问项的引用。 此示例可能代表一个简单的通讯簿，您可以在其中查找按姓氏的人员。

由于*密钥*参数的类型为 `CString` ，并且*KEY_TYPE*参数的类型为，因此 `LPCSTR` ，该键作为类型的项存储在映射中， `CString` 但在函数（如） `SetAt` 类型的指针之间引用 `LPCSTR` 。 例如：

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>使用类型指针集合模板

若要使用类型指针集合模板，你需要知道可以在这些集合中存储哪些类型的数据，以及要在集合声明中使用哪些参数。

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>类型化指针数组和列表用法

类型化指针数组和列表类[CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)和[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)采用两个参数： *BASE_CLASS*和*类型*。 这些类可以存储在*类型*参数中指定的任何数据类型。 它们派生自一个存储指针的非模板集合类;在*BASE_CLASS*中指定此基类。 对于数组，请使用 `CObArray` 或 `CPtrArray` 。 对于列表，请使用 `CObList` 或 `CPtrList` 。

实际上，当你声明基于的集合时， `CObList` 新类不仅继承其基类的成员，而且还声明了多个附加类型安全的成员函数和运算符，这些函数通过封装对基类成员的调用来帮助提供类型安全。 这些封装管理所有必要的类型转换。 例如：

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

第一个示例声明一个类型化的指针数组， `myArray` 派生自 `CObArray` 。 数组存储并返回指向对象的指针 `CPerson` （其中 `CPerson` 是派生自的类 `CObject` ）。 可以调用任何 `CObArray` 成员函数，也可以调用新的类型安全的 `GetAt` 和函数， `ElementAt` 或使用类型安全的 **[]** 运算符。

第二个示例声明派生自的类型指针列表 `myList` `CPtrList` 。 列表存储并返回指向对象的指针 `MY_STRUCT` 。 基于的类 `CPtrList` 用于存储指向不是派生自的对象的指针 `CObject` 。 `CTypedPtrList`具有多个类型安全的成员函数： `GetHead` 、 `GetTail` 、 `RemoveHead` 、、、 `RemoveTail` `GetNext` `GetPrev` 和 `GetAt` 。

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>类型化的指针映射用法

类型化指针映射类[CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)采用三个参数： *BASE_CLASS*、*键*和*值*。 *BASE_CLASS*参数指定派生新类的类：、、、、等 `CMapPtrToWord` `CMapPtrToPtr` `CMapStringToPtr` `CMapWordToPtr` `CMapStringToOb` 。 *键*类似于中*KEY*的键 `CMap` ：它指定用于查找的键的类型。 *值*类似于中*VALUE*的值 `CMap` ：它指定存储在映射中的对象的类型。 例如：

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

第一个示例是基于的映射 `CMapPtrToPtr` ，它使用 `CString` 映射到指向的指针的键 `MY_STRUCT` 。 可以通过调用类型安全的成员函数查找存储指针 `Lookup` 。 如果找不到，则可以使用 **[]** 运算符查找存储的指针并添加它。 您可以使用类型安全函数循环访问映射 `GetNextAssoc` 。 还可以调用类的其他成员函数 `CMapPtrToPtr` 。

第二个示例是基于的地图 `CMapStringToOb` ，它使用映射到对象的存储指针的字符串键 `CMyObject` 。 您可以使用上一段中所述的相同类型安全成员，也可以调用类的成员 `CMapStringToOb` 。

> [!NOTE]
> 如果为 **`class`** **`struct`** *值*形参指定或类型，而不是对类型的指针或引用指定，则类或结构必须具有复制构造函数。

有关详细信息，请参阅[如何建立类型安全的集合](../mfc/how-to-make-a-type-safe-collection.md)。

## <a name="see-also"></a>另请参阅

[集合](../mfc/collections.md)
