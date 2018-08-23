---
title: 关于选择集合类的建议 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- type safety of collection classes [MFC]
- collection classes [MFC], serialization
- collection classes [MFC], speed
- collection classes [MFC], type safety
- collection classes [MFC], choosing
- collection classes [MFC], functionality
- shapes, collection
- collection classes [MFC], template-based
- MFC collection classes [MFC], characteristics
- collection classes [MFC], about collection classes [MFC]
- serialization [MFC], collection classes
- collection classes [MFC], duplicates allowed
- collection classes [MFC], shapes
ms.assetid: a82188cd-443f-40d8-a244-edf292a53db4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28527f9668b9ca6a9ef00cf399a04ce9bad65716
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353127"
---
# <a name="recommendations-for-choosing-a-collection-class"></a>关于选择集合类的建议
本文包含旨在帮助你选择满足特定应用程序需求的集合类的详细信息。  
  
 你对集合类的选择取决于许多因素，包括：  
  
-   类形状的特征：顺序、索引和性能，正如本主题中 [Collection Shape Features（集合形状特征）](#_core_collection_shape_features) 表所示。  
  
-   类是否使用 C++ 模板  
  
-   存储在集合中的元素是否可以序列化  
  
-   存储在集合中的元素是否可以转储以供诊断  
  
-   集合是否为类型安全的  
  
 下表 [Collection Shape Features（集合形状特征）](#_core_collection_shape_features)总结了可用集合形状的特征。  
  
-   列 2 和 3 描述了每个形状的排序和访问特性。 在表中，术语“决定顺序”是指插入和删除项的顺序决定其在集合中的顺序；不是指项在其内容中的排序。 术语“索引检索”是指集合中的项可通过整数索引进行检索，这与典型数组中的项很相似。  
  
-   列 4 和 5 描述了每个形状的性能。 在需要多次插入集合的应用程序中，插入速度可能特别重要；而对于其他应用程序，查找速度可能更为重要。  
  
-   列 6 描述了每个形状是否允许重复元素。  
  
### <a name="_core_collection_shape_features"></a>  Collection Shape Features（集合形状特征）  
  
|形状|Ordered|编制索引|插入元素|搜索指定的元素|重复的元素|  
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|  
|列表|是|否|快速|缓慢|是|  
|数组|是|根据 int|缓慢|缓慢|是|  
|映射|否|根据键|快速|快速|否（键）是（值）|  
  
 下表 [Characteristics of MFC Collection Classes（MFC 集合类的特征）](#_core_characteristics_of_mfc_collection_classes)总结了特定 MFC 集合类的其他重要特征，可作为选择的指南。 你的选择可以取决于以下因素：类是否基于 C++ 模板，它的元素是否可通过 MFC 的文档 [序列化](../mfc/serialization-in-mfc.md) 机制进行序列化，它的元素是否可通过 MFC 的诊断转储机制进行转储，类是否是安全类型（也就是说，你是否能保证元素的类型存储在且检索自基于类的集合上）。  
  
### <a name="_core_characteristics_of_mfc_collection_classes"></a>  Characteristics of MFC Collection Classes（MFC 集合类的特征）  
  
|类|使用 C++<br /><br /> 模板|可以<br /><br /> 已序列化|可以<br /><br /> 转储|是<br /><br /> Type-Safe — 类型安全|  
|-----------|------------------------------|---------------------------|-----------------------|-----------------------|  
|`CArray`|是|是 1|是 1|否|  
|`CByteArray`|否|是|是|是 3|  
|`CDWordArray`|否|是|是|是 3|  
|`CList`|是|是 1|是 1|否|  
|`CMap`|是|是 1|是 1|否|  
|`CMapPtrToPtr`|否|否|是|No|  
|`CMapPtrToWord`|否|否|是|No|  
|`CMapStringToOb`|否|是|是|No|  
|`CMapStringToPtr`|否|否|是|No|  
|`CMapStringToString`|否|是|是|是 3|  
|`CMapWordToOb`|否|是|是|No|  
|`CMapWordToPtr`|否|否|是|No|  
|`CObArray`|否|是|是|No|  
|`CObList`|否|是|是|No|  
|`CPtrArray`|否|否|是|No|  
|`CPtrList`|否|否|是|No|  
|`CStringArray`|否|是|是|是 3|  
|`CStringList`|否|是|是|是 3|  
|`CTypedPtrArray`|是|取决于 2|是|是|  
|`CTypedPtrList`|是|取决于 2|是|是|  
|`CTypedPtrMap`|是|取决于 2|是|是|  
|`CUIntArray`|No|否|是|是 3|  
|`CWordArray`|否|是|是|是 3|  
  
 1. 要序列化，你必须明确地调用集合对象的`Serialize`函数; 要转储，必须显式调用其`Dump`函数。 不能使用表单 `ar << collObj` 来进行序列化或使用表单 `dmp` `<< collObj` 来进行转储。  
  
 2. 可序列化性取决于基础集合类型。 例如，如果类型化指针数组基于 `CObArray`，则可序列化；如果基于 `CPtrArray`，则不可序列化。 一般情况下，“Ptr”类不能进行序列化。  
  
 3. 如果在此列中标记为“是”，若你按要求使用它，则非模板集合类为类型安全。 例如，如果你在 `CByteArray`中存储字节，则数组为类型安全。 但如果你将其用于存储字符，则其类型安全性稍微不确定。  
  
## <a name="see-also"></a>请参阅  
 [集合](../mfc/collections.md)   
 [基于模板的类](../mfc/template-based-classes.md)   
 [如何： 创建类型安全集合](../mfc/how-to-make-a-type-safe-collection.md)   
 [访问集合的所有成员](../mfc/accessing-all-members-of-a-collection.md)

