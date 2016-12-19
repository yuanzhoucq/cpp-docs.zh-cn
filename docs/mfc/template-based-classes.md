---
title: "基于模板的类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 类"
  - "数组 [C++], 指针"
  - "数组 [C++], 基于模板的"
  - "CArray 类, 基于模板的类"
  - "CList 类, 基于模板的类"
  - "集合类, 基于模板的"
  - "集合, 类型化指针"
  - "CTypedPtrArray 类, 基于模板的类"
  - "CTypedPtrList 类, 基于模板的类"
  - "CTypedPtrMap 类, 基于模板的类"
  - "MFC 集合类, 基于模板的"
  - "指针, 类型化的集合"
  - "简单的数组集合类"
  - "简单的列表集合类"
  - "简单的基于模板的集合"
  - "基于模板的集合类"
  - "类型化指针"
  - "类型化指针, 集合"
  - "类型安全集合"
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 基于模板的类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文演示在 MFC 3.0 的类型安全基于模板的集合类和之后。  使用这些模板创建类型安全的集合更方便，并帮助比使用基于模板不提供的更有效类型安全集合类。  
  
 MFC 预定义基于模板的集合的两类：  
  
-   [简单的数组、列表以及映射类](#_core_using_simple_array.2c_.list.2c_.and_map_templates)  
  
     `CArray`, `CList`, `CMap`  
  
-   [类型化指针数组、列表、映射](#_core_using_typed.2d.pointer_collection_templates)  
  
     `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`  
  
 简单的集合类均从 `CObject`类派生，因此，它们继承序列化、动态创建和其他 `CObject`属性。  类型化指针集合类要求您指定从派生 \- 必须是 MFC 预定义的某一个指向集合，如 `CPtrList` 或 `CPtrArray`的类。  新集合类从指定的新基类和类的成员函数使用 sealed 调用继承于基类成员强制"类型安全。  
  
 有关 C\+\+ 模板的更多信息，请参见*C\+\+ 语言参考的*[模板](../cpp/templates-cpp.md)。  
  
##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> 使用简单的数组、列表以及映射模板  
 若要使用集合的简单模板，则需要知道使用哪种数据以及在这些集合可以存储，以及参数在集合声明。  
  
###  <a name="_core_simple_array_and_list_usage"></a> 简单数组和列表用法  
 简单数组和列表类，和 [CArray](../mfc/reference/carray-class.md)[CList](../mfc/reference/clist-class.md)，采用两个参数：*类型* 和 `ARG_TYPE`。  这些类可以存储任何数据类型，则可以在参数指定 *类型* :  
  
-   基本 C\+\+ 数据类型，如 `int`、`char`和 **浮动**  
  
-   C\+\+ 结构和类  
  
-   您可以定义的其他类型  
  
 为了方便起见和效率，您可以使用 `ARG_TYPE` 参数指定函数的参数类型。  通常，将 `ARG_TYPE` 指定为在 *类型* 参数中的类型的引用。  例如：  
  
 [!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/CPP/template-based-classes_1.cpp)]  
  
 第一个示例声明数组集合，`myArray`，包含 `int`s。  第二个示例声明列表集合，`myList`，以存储 `CPerson` 对象。  集合类的某些成员函数采用类型由 `ARG_TYPE` 模板参数指定的参数。  例如，`CArray` 类的 **添加** 成员函数采用 `ARG_TYPE` 参数：  
  
 [!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/CPP/template-based-classes_2.cpp)]  
  
###  <a name="_core_simple_map_usage"></a> 简单用法的映射  
 简单类的映射，[CMap](../mfc/reference/cmap-class.md)，采用四个参数：*键*、`ARG_KEY`，*值*和 `ARG_VALUE`。  与数组和列表类，类映射可以存储任何数据类型。  与数组不同和列表，索引和订单数据，它们存储映射与键和值：在将存储的值通过指定值关联的键。  *关键* 参数指定用于键的数据访问类型在将存储的数据。  如果 *键* 类型是结构或类，`ARG_KEY` 参数通常是指定为 *键*的类型的引用。  *值* 参数映射中指定存储项的类型。  如果 `ARG_VALUE` 的类型是结构或类，`ARG_VALUE` 参数通常是在对 *值*指定的类型的引用。  例如：  
  
 [!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/CPP/template-based-classes_3.cpp)]  
  
 第一个示例 `MY_STRUCT` 值由 `int` 存储，键访问它们，并通过引用返回访问的 `MY_STRUCT` 项。  第二个示例 `CPerson` 值由 `CString` 存储，键访问它们并访问的项返回引用。  此示例可能表示一个简单的消息，并且按姓查找用户。  
  
 因为 *关键* 参数的类型为 `CString`，它 *KEY\_TYPE* 参数的类型为 `LPCSTR`，键是在映射函数中都作为 `CString` 类型存储项，但引用 \( `SetAt` 类型通过 `LPCSTR`指针。  例如：  
  
 [!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/CPP/template-based-classes_4.cpp)]  
  
##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> 键入模板集合使用指针  
 要使用类型化指针集合模板，则需要知道使用哪种数据以及在这些集合可以存储，以及参数在集合声明。  
  
###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> 类型化指针数组和列表用法  
 类型化指针数组和列表类，和 [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)，采用两个参数：`BASE_CLASS` 和 *类型*。  这些类可以存储任何数据类型，则该 *类型* 参数指定。  它们从存储指针的其中一个集合类派生；在 `BASE_CLASS`指定此基类。  对于数组，请使用 `CObArray` 或 `CPtrArray`。  对于列表，请使用 `CObList` 或 `CPtrList`。  
  
 实际上，在中，如果您声明集合基于时，`CObList`中添加，新类不仅继承其基类的成员，即，但也声明大量额外的安全类型成员函数和运算符通过封装调用帮助提供类型安全并为基类成员。  封装这些管理所有必要的类型转换。  例如：  
  
 [!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/CPP/template-based-classes_5.cpp)]  
  
 第一个示例声明类型化指针数组，`myArray`，派生自 `CObArray`。  数组存储并返回指向 `CPerson` 对象 \(其中 `CPerson` 是从 `CObject`派生的类\)。  可以调用任何 `CObArray` 成员函数，或者可以调用新的类型安全函数 `GetAt` 和 `ElementAt` 或使用类型安全 \#\#\#\[\#\#\#\] 运算符。  
  
 第二个示例声明类型化指针，列表 `myList`，派生自 `CPtrList`。  列表存储并返回指向 `MY_STRUCT` 对象的指针。  基于 `CPtrList` 的类提供了用于存储到 `CObject`派生的对象的指针。  `CTypedPtrList` 有多个类型安全函数：成员 `GetHead`、`GetTail`、`RemoveHead`、`RemoveTail`、`GetNext`、`GetPrev`和 `GetAt`。  
  
###  <a name="_core_typed.2d.pointer_map_usage"></a> 类型化指针映射用法  
 映射类指针类型，[CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)，采用三个参数：`BASE_CLASS`、*键*和 *值*。  `BASE_CLASS` 参数指定派生新类的类：`CMapPtrToWord`，`CMapPtrToPtr`，`CMapStringToPtr`，`CMapWordToPtr`，`CMapStringToOb`，依此类推。  *键* 类似于 *键* 在 `CMap`中：它指定用于查找键的类型。  *值* 是类似的 *值* 在 `CMap`中：该映射指定存储的对象的类型。  例如：  
  
 [!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/CPP/template-based-classes_6.cpp)]  
  
 第一个示例是基于 **CMapPtrToPt**的映射 r \- 它使用 `CString` 键映射到指针为 `MY_STRUCT`。  通过调用类型安全函数搜索一个 `Lookup` 成员的指针。  可以使用 \#\#\#\[\#\#\#\] 运算符查找一个存储指针和添加它，如果没有找到。  使用类型安全函数 `GetNextAssoc`，并可以循环访问映射。  还可以调用 `CMapPtrToPtr`类的任何其他成员函数。  
  
 第二个示例是基于 **CMapStringToO**的映射目标 \- 它使用字符串键映射到存储的指针为 `CMyObject` 对象。  可以使用前面介绍段落的同样的类型安全成员，或者可以调用 `CMapStringToOb`类的成员。  
  
> [!NOTE]
>  如果对 *值* 参数指定 **类** 或 `struct` 类型，而不是指针或引用到类型，类或结构必须具有复制构造函数。  
  
 有关更多信息，请参见 [如何生成类型安全的集合](../mfc/how-to-make-a-type-safe-collection.md)。  
  
## 请参阅  
 [集合](../mfc/collections.md)