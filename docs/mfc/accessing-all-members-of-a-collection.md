---
title: 访问集合的所有成员 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, collections
- enumerations [MFC]
- enumerating collections [MFC]
- collections [MFC], accessing
- collection classes [MFC]
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
ms.assetid: 7bbae518-062e-4393-81f9-b22abd2e5f59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec9757a463bce7ef873720f229b70da695deae8d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-all-members-of-a-collection"></a>访问集合的所有成员
MFC 数组集合类（无论是否基于模板）使用索引来访问其元素。 MFC 列表和映射集合类（无论是否基于模板）使用 **POSITION** 类型的指示器来描述集合内的给定位置。 若要访问这些集合的一个或多个成员，首先初始化位置指示器，然后重复将此位置传递给集合，使其返回下一个元素。 集合不负责维护迭代进度的状态信息。 该信息保存在位置指示器。 但对于给定的特定位置，集合负责返回下一个元素。  
  
 下面的过程演示如何循环访问 MFC 提供的三种主要类型集合：  
  
-   [循环访问数组](#_core_to_iterate_an_array)  
  
-   [循环访问列表](#_core_to_iterate_a_list)  
  
-   [循环访问映射](#_core_to_iterate_a_map)  
  
### <a name="_core_to_iterate_an_array"></a> 循环访问数组  
  
1.  使用按次序的索引号与 `GetAt` 成员函数：  
  
     [!code-cpp[NVC_MFCCollections#12](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]  
  
     此示例使用一个类型化的指针数组，其中包含指向 `CPerson` 对象的指针。 数组派生自 `CObArray`类，这是一个非模板预定义类。 `GetAt` 返回一个指向 `CPerson` 对象的指针。 对于类型化的指针集合类（数组或列表），第一个参数指定基类；第二个参数指定要存储的类型。  
  
     `CTypedPtrArray`类还重载 **[]** 运算符，以便你可以使用常用的数组下标语法来访问数组的元素。 以上 `for` 循环正文中的语句的替代是  
  
     [!code-cpp[NVC_MFCCollections#13](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]  
  
     此运算符同时存在于 **常量** 和非**常量** 版本。 **常量** 版本（为 **常量** 数组调用）仅可在赋值语句右侧出现。  
  
### <a name="_core_to_iterate_a_list"></a> 循环访问列表  
  
1.  使用成员函数 `GetHeadPosition` 和 `GetNext` 来访问列表：  
  
     [!code-cpp[NVC_MFCCollections#14](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]  
  
     此示例使用一个类型化的指针列表，包含指向 `CPerson` 对象的指针。 列表声明类似于 [循环访问数组](#_core_to_iterate_an_array) 步骤中数组的列表声明，但它派生自 `CObList`类。 `GetNext` 返回一个指向 `CPerson` 对象的指针。  
  
### <a name="_core_to_iterate_a_map"></a> 循环访问映射  
  
1.  使用 `GetStartPosition` 来到映射的开头，使用 `GetNextAssoc` 反复获取映射中的下一个键和值，如下所示：  
  
     [!code-cpp[NVC_MFCCollections#15](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]  
  
     此示例使用简单的映射模板（而不是类型化的指针集合），该模板使用 `CString` 键，并存储指向 `CPerson` 对象的指针。 当使用访问函数（如 `GetNextAssoc`）时，该类提供了指向 `CPerson` 对象的指针。 如果改为使用非模板映射集合之一，则必须将返回的 `CObject` 指针转换为指向 `CPerson`的指针。  
  
    > [!NOTE]
    >  对于非模板映射，编译器需要最后一个 `CObject` 参数中 `GetNextAssoc`指针的引用。 在输入时，必须将指针转换为类型，如下例所示。  
  
     模板解决方案更简单，可帮助提高类型安全性。 非模板代码更复杂一些，正如你在这里看到的：  
  
     [!code-cpp[NVC_MFCCollections#16](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]  
  
 有关详细信息，请参阅 [删除 CObject 集合中的所有对象](../mfc/deleting-all-objects-in-a-cobject-collection.md)。  
  
## <a name="see-also"></a>请参阅  
 [集合](../mfc/collections.md)

