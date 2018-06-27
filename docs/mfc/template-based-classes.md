---
title: 基于模板的类 |Microsoft 文档
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
ms.openlocfilehash: 035a50e039b352775cf0f109310f4dac448cb0a1
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954642"
---
# <a name="template-based-classes"></a>基于模板的类
此文章介绍了 MFC 3.0 版及更高版本中的类型安全的基于模板的集合类。 使用这些模板创建类型安全的集合是更方便，并帮助比使用不基于模板的集合类更有效地提供类型安全。  
  
 MFC 预定义基于模板的集合的两个的类别：  
  
-   [简单的数组、 列表和映射类](#_core_using_simple_array.2c_.list.2c_.and_map_templates)  
  
     `CArray`, `CList`, `CMap`  
  
-   [数组、 列表和的类型化指针的映射](#_core_using_typed.2d.pointer_collection_templates)  
  
     `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`  
  
 简单的集合类都派生自类`CObject`，因此它们在继承序列化、 动态创建和其他属性`CObject`。 类型化的指针集合类要求你指定派生自的类，它必须是一个如由 MFC，预定义的非模板指针集合`CPtrList`或`CPtrArray`。 新的集合类继承自指定的基类，并用新类的成员函数封装到基类成员的调用来强制类型安全。  
  
 有关 c + + 模板的详细信息，请参阅[模板](../cpp/templates-cpp.md)中*c + + 语言参考*。  
  
##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> 使用简单的数组、 列表和映射模板  
 若要使用简单的集合模板，你需要知道可以在这些集合中存储什么类型的数据以及要在集合声明中使用的参数。  
  
###  <a name="_core_simple_array_and_list_usage"></a> 简单的数组和列表的用法  
 简单数组和列表类[CArray](../mfc/reference/carray-class.md)和[CList](../mfc/reference/clist-class.md)，采用两个参数：*类型*和`ARG_TYPE`。 这些类可以存储任何数据类型，它指定在*类型*参数：  
  
-   基本的 c + + 数据类型，如**int**， **char**，和**float**  
  
-   C + + 结构和类  
  
-   你定义其他类型  
  
 为了方便使用和效率，你可以使用*ARG_TYPE*参数来指定函数自变量的类型。 通常情况下，指定*ARG_TYPE*作为对你在名为的类型的引用*类型*参数。 例如：  
  
 [!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]  
  
 第一个示例声明的数组集合、 `myArray`，包含**int**s。 第二个示例声明列表集合， `myList`，存储`CPerson`对象。 集合类的某些成员函数采用其类型由指定的自变量*ARG_TYPE*模板参数。 例如，`Add`类的成员函数`CArray`采用*ARG_TYPE*自变量：  
  
 [!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]  
  
###  <a name="_core_simple_map_usage"></a> 简单的映射使用情况  
 简单的映射类， [CMap](../mfc/reference/cmap-class.md)，采用四个参数：*密钥*， *ARG_KEY*，*值*，和*ARG_VALUE*. 数组和列表像类一样，映射类可以存储任何数据类型。 数组和列表，其中索引和排序它们在存储的数据，与地图关联键和值： 访问存储在映射中通过指定的值关联的键的值。 *密钥*参数指定用于访问存储在映射中的数据的键的数据类型。 如果的一种*密钥*是结构或类， *ARG_KEY*参数通常是对中指定的类型的引用*密钥*。 *值*参数指定映射中存储的项的类型。 如果的一种*ARG_VALUE*是结构或类， *ARG_VALUE*参数通常是对中指定的类型的引用*值*。 例如：  
  
 [!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]  
  
 第一个示例存储`MY_STRUCT`值、 访问通过它们**int**密钥，并返回访问`MY_STRUCT`通过引用的项。 第二个示例存储`CPerson`值、 访问通过它们`CString`键，并返回对访问的项的引用。 该示例可以表示简单的通讯簿，在其中你查找人员按姓氏。  
  
 因为*密钥*形参属于类型`CString`和*KEY_TYPE*形参属于类型`LPCSTR`，密钥存储在映射的类型的项`CString`但中引用函数如`SetAt`类型的指针通过`LPCSTR`。 例如：  
  
 [!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]  
  
##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> 使用类型化指针集合模板  
 若要使用的类型化指针集合模板，你需要知道可以在这些集合中存储什么类型的数据和要在集合声明中使用的参数。  
  
###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> 类型化指针数组和列表的用法  
 类型化指针数组和列表类[CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)和[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)，采用两个参数： *BASE_CLASS*和*类型*。 这些类可以存储任何数据类型，它指定在*类型*参数。 它们派生自其中一个存储指针; 的非模板集合类指定在此基类*BASE_CLASS*。 对于数组，使用两种`CObArray`或`CPtrArray`。 对于列表，请使用两种`CObList`或`CPtrList`。  
  
 实际上，在声明时基于的集合，比如`CObList`、 新类不仅继承其基本类的成员，但它还声明大量的其他类型安全成员函数和帮助通过封装提供类型安全的运算符对基类成员的调用。 这些封装管理所有必要的类型转换。 例如：  
  
 [!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]  
  
 第一个示例声明的类型化指针数组，`myArray`派生自`CObArray`。 数组存储并返回指向`CPerson`对象 (其中`CPerson`类派生自`CObject`)。 你可以调用任意`CObArray`成员函数，或你可以调用新的类型安全`GetAt`和`ElementAt`函数或使用类型安全 **[]** 运算符。  
  
 第二个示例声明的类型化指针列表，`myList`派生自`CPtrList`。 列表存储并返回指向`MY_STRUCT`对象。 类根据`CPtrList`用于存储指向不派生自的对象的指针`CObject`。 `CTypedPtrList` 具有大量类型安全成员函数： `GetHead`， `GetTail`， `RemoveHead`， `RemoveTail`， `GetNext`， `GetPrev`，和`GetAt`。  
  
###  <a name="_core_typed.2d.pointer_map_usage"></a> 类型化指针映射的用法  
 类型化指针映射类， [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)，采用三个参数： *BASE_CLASS*，*密钥*，和*值*。 *BASE_CLASS*参数指定从中派生新类的类： `CMapPtrToWord`， `CMapPtrToPtr`， `CMapStringToPtr`， `CMapWordToPtr`， `CMapStringToOb`，依次类推。 *密钥*类似于*密钥*中`CMap`： 它指定用于查找的键的类型。 *值*类似于*值*中`CMap`： 它指定的对象存储在映射的类型。 例如：  
  
 [!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]  
  
 第一个示例是基于映射`CMapPtrToPtr`-它使用`CString`键映射到指向`MY_STRUCT`。 可以通过调用安全类型来查找存储的指针`Lookup`成员函数。 你可以使用 **[]** 运算符来查找存储的指针并将其添加如果不是找到。 可循环使用类型安全的映射和`GetNextAssoc`函数。 你还可以调用其他成员函数的类`CMapPtrToPtr`。  
  
 第二个示例是基于映射`CMapStringToOb`-它使用映射到存储指向的字符串键`CMyObject`对象。 你可以使用前面的段落中所述相同的类型安全成员也可以调用类的成员`CMapStringToOb`。  
  
> [!NOTE]
>  如果指定**类**或**结构**键入*值*参数，而不是指针或引用类型、 类或结构必须具有复制构造函数。  
  
 有关详细信息，请参阅[如何生成类型安全集合](../mfc/how-to-make-a-type-safe-collection.md)。  
  
## <a name="see-also"></a>请参阅  
 [集合](../mfc/collections.md)

