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
ms.openlocfilehash: f1b59516d5bba13b6f5e006f91d8ebd560543b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372149"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>通过存档存储和加载 CObject

通过存档存储`CObject`和加载 s 需要额外考虑。 在某些情况下，`Serialize`应调用对象的函数，其中`CArchive`对象是调用的`Serialize`参数，而不是使用 的**<** 或**>>** 运算符`CArchive`。 需要记住的重要事实是，`CArchive`**>>** 运算符根据`CObject``CRuntimeClass`以前由存储存档写入文件的信息构造内存中。

因此，使用`CArchive`**<** 和**>>** 运算符与调用`Serialize`*取决于是否需要加载*存档基于以前存储`CRuntimeClass`的信息动态重建对象。 在以下`Serialize`情况下使用函数：

- 当对对象进行反序列化时，您事先知道对象的确切类。

- 在反序列化对象时，已为其分配了内存。

> [!CAUTION]
> 如果使用 函数加载对象`Serialize`，则还必须使用 函数`Serialize`存储对象。 不要使用运算符进行存储，`CArchive`**<<** 然后使用`Serialize`函数加载，或使用函数存储，`Serialize`然后使用`CArchive >>`运算符加载。

下面的示例说明了以下情况：

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

`CObject`总之，如果可序列化类将嵌入定义为成员，*则不应*对该对象使用`CArchive`**<** 和**>>** 运算符，而应改为调用`Serialize`函数。 此外，如果可序列化类将指向 （`CObject`或派生自`CObject`） 的对象的指针定义为成员，但在其自己的构造函数中构造此其他对象，则还应调用`Serialize`。

## <a name="see-also"></a>另请参阅

[序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)
