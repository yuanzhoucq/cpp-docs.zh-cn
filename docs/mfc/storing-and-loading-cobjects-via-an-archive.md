---
title: 通过存档存储和加载 CObject
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: 591ce7032aa3d70b1e5a020cd9173ed4c9d0fa9b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299936"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>通过存档存储和加载 CObject

存储和加载`CObject`s 通过存档需要额外的注意事项。 在某些情况下，应调用`Serialize`函数的对象，其中`CArchive`对象为的参数`Serialize`调用，而不是使用**< \<** 或**>>** 运算符的`CArchive`。 要记住的重要事实是， `CArchive` **>>** 运算符构造`CObject`基于内存中`CRuntimeClass`以前由存储存档写入到文件的信息。

因此，是否使用`CArchive` **< \<** 并**>>** 运算符，而不是调用`Serialize`，取决于是否您*需要*加载存档动态地重新构造该对象基于以前存储`CRuntimeClass`信息。 使用`Serialize`函数在以下情况下：

- 当反序列化对象，您预先知道对象的具体类。

- 当反序列化对象，你已经为其分配的内存。

> [!CAUTION]
>  如果加载对象使用`Serialize`函数，还必须存储对象使用`Serialize`函数。 不会存储使用`CArchive` **<<** 运算符，然后负载使用`Serialize`函数，或使用存储`Serialize`函数，然后加载使用`CArchive >>`运算符。

下面的示例阐释了这些情况：

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

总之，如果可序列化类定义嵌入`CObject`作为一名成员，你应该*不*使用`CArchive` **< \<** 和 **>>** 运算符，该对象，但应调用`Serialize`函数。 此外，如果可序列化类定义一个指向`CObject`(或一个派生自`CObject`) 作为一名成员，但构造此其他对象在自己的构造函数，您还应调用`Serialize`。

## <a name="see-also"></a>请参阅

[序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)
