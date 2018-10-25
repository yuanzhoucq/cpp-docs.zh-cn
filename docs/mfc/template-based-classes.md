---
title: 基于模板的类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b972d4552a8e41ca0dcea4ef57d48ef161ea35b9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069225"
---
# <a name="template-based-classes"></a>基于模板的类

本文介绍了 MFC 3.0 版及更高版本中的类型安全的基于模板的集合类。 使用这些模板来创建类型安全集合是更方便，并帮助提供类型安全效率比使用不基于模板的集合类。

MFC 预定义了两种类别的基于模板的集合：

- [简单数组、 列表和映射类](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [数组、 列表和的类型化指针的映射](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

简单的集合类都派生自类`CObject`，因此它们继承序列化、 动态创建和其他属性`CObject`。 类型化的指针集合类需要你指定从派生的类，它必须是一个预定义 mfc，如非模板指针集合`CPtrList`或`CPtrArray`。 新集合类继承自指定的基类，并用新类的成员函数对基类成员的封装的调用来强制实施类型安全性。

有关 c + + 模板的详细信息，请参阅[模板](../cpp/templates-cpp.md)中*c + + 语言参考*。

##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> 使用简单的数组、 列表和映射模板

若要使用简单集合模板，您需要知道可以在这些集合中存储的数据类型和要在集合声明中使用的参数。

###  <a name="_core_simple_array_and_list_usage"></a> 简单数组和列表的用法

简单数组和列表类[CArray](../mfc/reference/carray-class.md)并[CList](../mfc/reference/clist-class.md)，采用两个参数：*类型*和`ARG_TYPE`。 这些类可以存储任何数据类型，在中指定*类型*参数：

- 基本的 c + + 数据类型，如**int**， **char**，和**float**

- C + + 结构和类

- 您定义其他类型

为方便起见和效率，您可以使用*ARG_TYPE*参数来指定函数参数的类型。 通常情况下，指定*ARG_TYPE*作为对中名为的类型的引用*类型*参数。 例如：

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

第一个示例声明数组集合`myArray`，，其中包含**int**s。 第二个示例声明列表集合`myList`，用于存储`CPerson`对象。 集合类的某些成员函数采用其类型由指定的自变量*ARG_TYPE*模板参数。 例如，`Add`类的成员函数`CArray`采用*ARG_TYPE*参数：

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

###  <a name="_core_simple_map_usage"></a> 简单的地图使用情况

简单的地图类[CMap](../mfc/reference/cmap-class.md)，采用四个参数：*密钥*， *ARG_KEY*，*值*，和*ARG_VALUE*. Array 和 list 像类一样，映射类可以存储任何数据类型。 与数组和列表，这些索引和排序它们存储的数据，不同映射关联键和值： 访问存储在映射中的指定值的关联的键的值。 *密钥*参数指定用来访问数据存储在映射中的键的数据类型。 如果类型*键*是结构或类， *ARG_KEY*参数通常是对中指定的类型的引用*密钥*。 *值*参数指定映射中存储的项的类型。 如果类型*ARG_VALUE*是结构或类， *ARG_VALUE*参数通常是对中指定的类型的引用*值*。 例如：

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

第一个示例存储`MY_STRUCT`值，通过它们访问**int**键，并返回访问`MY_STRUCT`通过引用的项。 第二个示例存储`CPerson`值，通过它们访问`CString`键，并返回对访问项的引用。 此示例中可能表示简单通讯簿中，在其中您查找人员的姓氏。

因为*键*参数的类型是`CString`并*KEY_TYPE*参数的类型是`LPCSTR`，密钥存储在映射类型的项作为`CString`但中引用之类的函数`SetAt`类型的指针通过`LPCSTR`。 例如：

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> 使用类型化指针集合模板

若要使用的类型化指针集合模板，您需要知道可以在这些集合中存储什么类型的数据和要在集合声明中使用的参数。

###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> 类型化指针数组和列表的用法

类型化指针数组和列表类[CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)并[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)，采用两个参数： *BASE_CLASS*并*类型*。 这些类可以存储任何数据类型，在中指定*类型*参数。 它们派生自其中一个存储指针; 的非模板集合类指定在此基类*BASE_CLASS*。 对于数组，使用两种`CObArray`或`CPtrArray`。 对于列表，请使用两种`CObList`或`CPtrList`。

实际上，在声明时基于的集合，说`CObList`，新类不仅继承其基类的成员，但它还声明许多其他类型安全成员函数和运算符，帮助通过封装提供类型安全对基类成员的调用。 这些封装管理所有必要的类型转换。 例如：

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

第一个示例声明了类型化指针数组`myArray`派生自`CObArray`。 该数组存储，并返回指向`CPerson`对象 (其中`CPerson`类派生自`CObject`)。 你可以调用任意`CObArray`成员函数，也可以调用新的类型安全`GetAt`并`ElementAt`函数，或使用类型安全 **[]** 运算符。

第二个示例声明了类型化指针列表中，`myList`派生自`CPtrList`。 该列表存储，并返回指向`MY_STRUCT`对象。 类根据`CPtrList`用于存储指向不是派生自的对象的指针`CObject`。 `CTypedPtrList` 具有多个类型安全成员函数： `GetHead`， `GetTail`， `RemoveHead`， `RemoveTail`， `GetNext`， `GetPrev`，和`GetAt`。

###  <a name="_core_typed.2d.pointer_map_usage"></a> 类型化指针映射的用法

类型化指针映射类[CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)，采用三个参数： *BASE_CLASS*，*密钥*，以及*值*。 *BASE_CLASS*参数指定的类从其派生新类： `CMapPtrToWord`， `CMapPtrToPtr`， `CMapStringToPtr`， `CMapWordToPtr`， `CMapStringToOb`，依次类推。 *键*类似于*密钥*中`CMap`： 它指定用于查找的键的类型。 *值*类似于*值*中`CMap`： 它指定的对象存储在映射中的类型。 例如：

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

第一个示例是基于地图`CMapPtrToPtr`— 它使用`CString`密钥映射到指向`MY_STRUCT`。 您可以查找存储的指针通过调用类型安全`Lookup`成员函数。 可以使用 **[]** 运算符来查找存储的指针并将其添加如果找不到。 您可以循环访问映射使用类型安全和`GetNextAssoc`函数。 您还可以调用其他成员函数的类`CMapPtrToPtr`。

第二个示例是基于地图`CMapStringToOb`— 它使用字符串键映射到存储指向`CMyObject`对象。 可以使用在上一段中所述的相同类型安全成员也可以调用类的成员`CMapStringToOb`。

> [!NOTE]
>  如果指定**类**或**结构**类型*值*参数，而不是指针或引用类型、 类或结构必须具有一个复制构造函数。

有关详细信息，请参阅[如何创建类型安全集合](../mfc/how-to-make-a-type-safe-collection.md)。

## <a name="see-also"></a>请参阅

[集合](../mfc/collections.md)

