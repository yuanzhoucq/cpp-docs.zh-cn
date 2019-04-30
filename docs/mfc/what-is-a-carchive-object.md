---
title: 什么是 CArchive 对象
ms.date: 11/04/2016
f1_keywords:
- CArchive
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 4bae451168449ce3e120ba9d172a615864ac2157
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346383"
---
# <a name="what-is-a-carchive-object"></a>什么是 CArchive 对象

`CArchive` 对象提供类型安全缓冲机制，以通过 `CFile` 对象写入或读取可序列化对象。 `CFile` 对象一般表示磁盘文件；但是，它还可能是可能表示剪贴板的内存文件（`CSharedFile` 对象）。

特定 `CArchive` 对象将存储（写入、序列化）数据或加载（读取、反序列化）数据，但不会同时进行这两种操作。 `CArchive` 对象的生命限制为将对象写入文件或从文件读取对象一次。 因此，两个连续创建的 `CArchive` 对象需要将数据序列化到文件，然后从文件将数据反序列化。

存档将对象存储到文件后，存档会将 `CRuntimeClass` 名称附加到对象。 然后，当另一个存档将对象从文件加载到内存时，`CObject` 派生的对象均将基于对象的 `CRuntimeClass` 动态重建。 给定对象在由存储存档写入文件后，可能被多次引用。 但是，加载存档将仅重建对象一次。 有关存档的将附加的详细信息`CRuntimeClass`对对象和重建对象，考虑到可能多个引用的信息中所述[技术说明 2](../mfc/tn002-persistent-object-data-format.md)。

当数据序列化到存档时，存档将累计数据直至缓冲区已满。 然后存档会将其缓冲区写入 `CFile` 对象所指向的 `CArchive` 对象。 同样，当您从存档读取数据时，会将数据从文件读取到其缓冲区，然后从缓冲区读取到您的反序列化对象。 此缓冲将减少物理读取硬盘的次数，从而提高应用程序的性能。

## <a name="see-also"></a>请参阅

[序列化：序列化对象](../mfc/serialization-serializing-an-object.md)
