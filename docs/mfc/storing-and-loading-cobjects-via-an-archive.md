---
title: 通过存档存储和加载 CObject
ms.date: 11/04/2016
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: 368421a86d6ff6fc70455edd0ea9a32e05645007
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446363"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>通过存档存储和加载 CObject

通过存档存储和加载 `CObject`需要额外考虑。 在某些情况下，应调用对象的 `Serialize` 函数，其中 `CArchive` 对象是 `Serialize` 调用的参数，而不是使用 \<的 **<>>** 或 **`CArchive`** 运算符。 需要记住的重要一点是，`CArchive` **>>** 运算符基于之前通过存储存档写入文件的 `CRuntimeClass` 信息来构造内存中的 `CObject`。

因此，无论你使用 `CArchive` **<\<** 和 **>>** 运算符，还是调用 `Serialize`，都取决于你是否*需要*加载存档以便基于以前存储的 `CRuntimeClass` 信息动态重建对象。 在以下情况下使用 `Serialize` 函数：

- 反序列化对象时，您事先知道对象的确切类。

- 反序列化对象时，已为其分配内存。

> [!CAUTION]
>  如果使用 `Serialize` 函数加载对象，则还必须使用 `Serialize` 函数来存储对象。 不要使用 `CArchive` **<<** 运算符存储，然后使用 `Serialize` 函数进行加载，或者使用 `Serialize` 函数进行存储，然后使用 `CArchive >>` 运算符加载。

下面的示例阐释了这种情况：

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

总之，如果可序列化类将嵌入的 `CObject` 定义为成员，则*不*应使用该对象的 `CArchive` **<\<** 和 **>>** 运算符，但应改为调用 `Serialize` 函数。 此外，如果可序列化的类将指向 `CObject` （或从 `CObject`派生的对象）的指针定义为成员，但在其自己的构造函数中构造此其他对象，则还应调用 `Serialize`。

## <a name="see-also"></a>另请参阅

[序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)
