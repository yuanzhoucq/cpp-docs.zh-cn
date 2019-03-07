---
title: 删除 CObject 集合中的所有对象
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
ms.openlocfilehash: 95d4cec61b230df5a019655617a25b1dc309cde4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257964"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>删除 CObject 集合中的所有对象

本文介绍如何删除集合中的所有对象（而不删除集合对象本身）。

若要删除的集合中的所有对象`CObject`s (或派生自`CObject`)，使用本文所述的迭代方法之一[访问的集合的所有成员](../mfc/accessing-all-members-of-a-collection.md)删除中的每个对象打开。

> [!CAUTION]
>  集合中的对象可以共享。 也就是说，集合将保留指向对象的指针，但程序的其他部分也可能具有指向同一对象的指针。 在使用共享对象删除所有部分之前，您必须小心以免删除此对象。

本文演示如何在下列内容中删除对象：

- [列表](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [一个数组](#_core_to_delete_all_elements_in_an_array)

- [映射](#_core_to_delete_all_elements_in_a_map)

#### <a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>  若要删除指向 CObject 的指针的列表中的所有对象

1. 使用 `GetHeadPosition` 和 `GetNext` 循环访问该列表。

1. 使用**删除**运算符删除迭代中遇到的每个对象。

1. 在删除与列表中所有元素关联的对象之后，调用 `RemoveAll` 函数删除这些元素。

以下示例演示如何删除 `CPerson` 对象列表中的所有对象。 列表中的每个对象都是指向最初在堆上分配的 `CPerson` 对象的指针。

[!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

最后一个函数调用 `RemoveAll` 是删除列表中所有元素的成员函数列表。 成员函数 `RemoveAt` 将删除单个元素。

请注意删除元素的对象和删除元素本身之间的区别。 删除列表中的元素将仅删除列表对对象的引用。 对象仍存在于内存中。 删除对象后，它将停止存在，并且将回收其内存。 因此，在删除元素的对象后立即删除元素很重要，这样一来列表才不会尝试访问不再存在的对象。

#### <a name="_core_to_delete_all_elements_in_an_array"></a>  若要删除数组中的所有元素

1. 使用 `GetSize` 和整数索引值循环访问数组。

1. 使用**删除**运算符删除迭代中遇到的每个元素。

1. 在删除数组中的所有元素后，调用 `RemoveAll` 函数从数组中移除这些元素。

   删除数组所有元素的代码如下所示：

   [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

与上述列表示例一样，您可调用 `RemoveAll` 删除数组中的所有元素或调用 `RemoveAt` 删除独立元素。

#### <a name="_core_to_delete_all_elements_in_a_map"></a> 若要删除映射中的所有元素

1. 使用 `GetStartPosition` 和 `GetNextAssoc` 循环访问数组。

1. 使用**删除**运算符删除迭代中遇到的密钥和/或每个地图元素的值。

1. 在删除映射中的所有元素后，调用 `RemoveAll` 函数从映射中移除这些元素。

   删除 `CMap` 集合的所有元素的代码如下所示。 映射中每个元素都具有一个作为键的字符串和一个作为值的 `CPerson` 对象（派生自 `CObject`）。

   [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

您可以调用 `RemoveAll` 删除映射中的所有元素或调用 `RemoveKey` 删除具有指定键的独立元素。

## <a name="see-also"></a>请参阅

[访问集合的所有成员](../mfc/accessing-all-members-of-a-collection.md)
