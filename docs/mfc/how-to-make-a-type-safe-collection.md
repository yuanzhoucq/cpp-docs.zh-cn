---
title: "如何：创建类型安全集合 | Microsoft Docs"
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
  - "集合类, 派生自非模板"
  - "集合类, 基于模板的"
  - "集合类, 类型安全"
  - "序列化 [C++], 集合类"
  - "SerializeElements 函数"
  - "序列化集合类元素"
  - "类型安全集合"
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
caps.latest.revision: 10
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：创建类型安全集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文演示如何进行类型安全"的集合自己的数据类型。  主题包括：  
  
-   [使用安全类型的基于模板的类](#_core_using_template.2d.based_classes_for_type_safety)  
  
-   [实现帮助程序函数](#_core_implementing_helper_functions)  
  
-   [使用非模板集合类](#_core_using_nontemplate_collection_classes)  
  
 Microsoft 基础类 \(MFC\) 库的基于 C\+\+ 模板的预定义类型安全的集合。  由于它们是模板，这些类有助于提供中为此使用非模板类和易用性，而模型模拟和其他额外操作中涉及的类型安全性。  MFC 示例使用 [收集](../top/visual-cpp-samples.md) 演示在 MFC 应用程序的基于模板的集合类。  通常，在这种情况下，在编写新代码的集合后，请使用这些类。  
  
##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> 使用安全类型的基于模板的类  
  
#### 若要使用模板基于类  
  
1.  声明集合类的类型的变量。  例如：  
  
     [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_1.cpp)]  
  
2.  调用集合对象的成员函数。  例如：  
  
     [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_2.cpp)]  
  
3.  如有必要，请实现和 [Helper 函数](../mfc/reference/collection-class-helpers.md) [SerializeElements](../Topic/SerializeElements.md)。  有关实现这些功能的信息，请参见 [实现 Helper 函数](#_core_implementing_helper_functions)。  
  
 此示例显示整数列表的声明。  在步骤 1 中的第一个参数是作为列表的元素存储的数据类型。  第二个参数指定这些数据如何将传递到并从集合类中的成员函数返回，如 **添加** 和 `GetAt`。  
  
##  <a name="_core_implementing_helper_functions"></a> 实现帮助程序函数  
 基于模板的集合类 `CArray`、`CList`和可自定义。需要对派生的类的 `CMap` 集合使用五全局 Helper 函数。  有关这些帮助程序函数的信息，请参见在 *MFC 参考"中的*[集合类帮助器](../mfc/reference/collection-class-helpers.md)。  序列化函数的实现需要为使用基于模板的集合类的大多数使用。  
  
###  <a name="_core_serializing_elements"></a> 序列化元素  
 `CArray`、`CList`和 `CMap` 类从存档调用 `SerializeElements` 来存储集合元素为或读取它们。  
  
 `SerializeElements` 帮助程序函数的默认实现位执行按位从对象的写入、存档或从存档的读取到对象，根据对象是否存储或从存档检索。  则此操作不合适，请重写 `SerializeElements`。  
  
 如果集合存储从 `CObject` 派生的对象，可以在集合元素类的实现使用 `IMPLEMENT_SERIAL` 宏，可以使用序列化功能内置于 `CArchive` 和 `CObject`:  
  
 [!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_3.cpp)]  
  
 `CArchive` 重载的运算符插入调用 `CObject::Serialize` \(或该函数\) 重写每个 **CPerson** 对象。  
  
##  <a name="_core_using_nontemplate_collection_classes"></a> 使用非模板集合类  
 MFC 还支持集合类引入与 MFC 版本 1.0。  这些类都不是基于模板的。  它们只用于包含支持的类型 `CObject*`、**UINT**、`DWORD`和 `CString`的数据。  可以使用这些预定义的集合 \(例如 `CObList`\) 包含所有从 `CObject`派生的对象的集合。  MFC 还提供其他预定义集合存储基元类型 \(如 **UINT** 和无效指针 \(`void`\*\)。  但一般来说，定义自己保存安全集合类型更具体的类及其派生列表的对象往往很有用的。  请注意使用基于模板的类，这样做不使用基于模板的集合类。更多工作比。  
  
 有两种创建一个集合类型安全"的集合：  
  
1.  使用个集合，而且类型如果需要，转换。  这是最容易的方法。  
  
2.  派生自并且扩展个类型安全的集合。  
  
#### 使用类型强制转换的非模板集合  
  
1.  使用某一个类，例如 `CWordArray`，直接。  
  
     例如，可以创建 `CWordArray` 并将所有 32 位值。它，然后检索。  无。  使用预定义功能。  
  
     也可以使用预定义集合，例如 `CObList`，不保存任何对象从 `CObject`派生。  `CObList` 集合中定义保存指向 `CObject`的指针。  当从列表中检索对象，则可能必须将结果强制转换为适当的类型，因为 `CObList` 函数返回指向 `CObject`。  例如，在中，如果存储在 `CObList` 集合中的 `CPerson` 对象，则必须将一检索元素的是指向 `CPerson` 对象。  下面的示例使用 `CObList` 集合都存储 `CPerson` 对象：  
  
     [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_4.cpp)]  
  
     此方法根据需要使用预定义的和集合类型转换可能满足许多集合需要。  如果您需要的功能或多种类型安全，请使用基于模板的类或者按照下一个过程。  
  
#### 要派生自并且扩展个类型安全的集合。  
  
1.  派生自己的从一个集合类预定义的非模板类。  
  
     当派生类时，可以添加类型安全包装函数提供一个类型安全接口以现有函数。  
  
     例如，在中，如果要从 `CObList` 派生一列表保存 `CPerson` 对象，可能将包装函数 `AddHeadPerson` 和 `GetHeadPerson`，如下所示。  
  
     [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_5.h)]  
  
     这些包装函数提供一个类型安全方法派生的列表添加和检索 `CPerson` 对象。  您可以查看已为 `GetHeadPerson` 函数，您密封了类型强制。  
  
     可以通过定义带有集合功能扩展而不是包装在类型安全包装中的现有功能中的新功能或添加新功能。  例如，[删除在 CObject 集合的所有对象](../mfc/deleting-all-objects-in-a-cobject-collection.md) 文章介绍的函数删除列表中包含的所有对象。  此功能无法添加到派生类的成员函数。  
  
## 请参阅  
 [集合](../mfc/collections.md)