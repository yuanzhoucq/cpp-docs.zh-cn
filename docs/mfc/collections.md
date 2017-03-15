---
title: "集合 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组模板"
  - "数组 [C++], 类"
  - "集合类, 关于集合类"
  - "集合类, 数组"
  - "集合类, 列表"
  - "集合类, 映射"
  - "集合类, MFC"
  - "集合类, 形状"
  - "集合类, 基于模板的"
  - "集合, 关于集合"
  - "MFC 集合类"
  - "MFC, 集合"
  - "形状"
  - "形状, 集合"
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类 \(MFC\) 库提供集合类管理对象组成的组。  这些类包括两种类型：  
  
-   [从 C\+\+ 模板的集合类创建](#_core_the_template.2d.based_collection_classes)  
  
-   [集合类不从模板创建](#_core_the_collection_classes_not_based_on_templates)  
  
> [!NOTE]
>  如果代码已使用个集合类，则可以继续使用它们。  如果在编写新类型安全"的集合类提供自己的数据类型，但我们推荐使用较新的基于模板的类。  
  
##  <a name="_core_collection_shapes"></a> 集合形状  
 集合类加上其“shape”和通过其元素类型。  形状引用对象由集合组织并存储的情况下。  MFC 提供三个简单的集合形态：列表、数组以及映射字典 \(也称为\)。  可以选取最适合于特定编程问题的集合形态。  
  
 三提供的集合形态每个本主题后面简要介绍。  若要比较形状的功能帮助您确定要对程序是最好，请参见 [关于选择集合类的建议](../mfc/recommendations-for-choosing-a-collection-class.md)。  
  
-   List  
  
     列表类提供元素的排序，为列表，实现为双向链接列表。  列表具有“头”，而且“尾”，并添加或移除元素。开头或末尾或插入或删除元素在中间，非常快。  
  
-   数组  
  
     数组类提供动态调整大小中，排序和整数索引的数组对象。  
  
-   映射 \(也是一个字典\)  
  
     映射是与的主要对象的值对象的集合。  
  
##  <a name="_core_the_template.2d.based_collection_classes"></a> 基于模板的集合类  
 简单的方法实现包含任何类型的对象类型安全的集合将使用某个基于 MFC 模板的类。  有关这些类的示例，请参见 MFC 示例 [收集](../top/visual-cpp-samples.md)。  
  
 下表列出了基于 MFC 模板的集合类。  
  
### 模板集合类  
  
|集合内容|数组|列表|映射|  
|----------|--------|--------|--------|  
|任何类型的对象的集合。|`CArray`|`CList`|`CMap`|  
|指针的任何对象的类型化集合|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|  
  
##  <a name="_core_the_collection_classes_not_based_on_templates"></a> 没有基于模板的集合类  
 如果应用已经使用MFC非模板类，则可以继续使用它们。  但是，对新的集合，建议使用基于模板的类。  下表列出了 MFC 不基于模板的集合类。  
  
### 非模板和集合类  
  
|数组|列表|映射|  
|--------|--------|--------|  
|`CObArray`|`CObList`|`CMapPtrToWord`|  
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|  
|`CDWordArray`|`CStringList`|`CMapStringToOb`|  
|`CPtrArray`||`CMapStringToPtr`|  
|`CStringArray`||`CMapStringToString`|  
|`CWordArray`||`CMapWordToOb`|  
|`CUIntArray`||`CMapWordToPtr`|  
  
 MFC 集合在 [关于选择集合类的建议](../mfc/recommendations-for-choosing-a-collection-class.md) 的类特性的表介绍 MFC 集合类。这些特性 \(除外\) 形状：  
  
-   类是使用 C\+\+ 模板  
  
-   在集合中的元素是可序列化  
  
-   集合中存储的元素是否可以为诊断转储  
  
-   集合是否是类型安全  
  
### 你希望做什么？  
  
#### 泛型集合类任务  
  
-   [关于选择集合类的建议](../mfc/recommendations-for-choosing-a-collection-class.md)  
  
-   [如何：创建类型安全集合](../mfc/how-to-make-a-type-safe-collection.md)  
  
-   [创建堆栈和队列集合](../mfc/creating-stack-and-queue-collections.md)  
  
-   [CArray::Add](../Topic/CArray::Add.md)  
  
#### 基于模板的集合类任务  
  
-   [基于模板的类](../mfc/template-based-classes.md)  
  
#### 访问集合的成员 \(基于模板\)  
  
-   [访问集合的所有成员](../mfc/accessing-all-members-of-a-collection.md)  
  
-   [删除 CObject 集合中的所有对象](../mfc/deleting-all-objects-in-a-cobject-collection.md)  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)