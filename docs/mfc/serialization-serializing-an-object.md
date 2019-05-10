---
title: 序列化：对象的序列化
ms.date: 11/04/2016
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
ms.openlocfilehash: 5c1106f180c587894283575a82a88e9e18b5c01a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308038"
---
# <a name="serialization-serializing-an-object"></a>序列化：对象的序列化

文章[序列化：定义可序列化的类](../mfc/serialization-making-a-serializable-class.md)演示如何使类可序列化。 可序列化类后，可以序列化该类与通过文件的对象[CArchive](../mfc/reference/carchive-class.md)对象。 本文介绍：

- [CArchive 对象是](../mfc/what-is-a-carchive-object.md)。

- [创建 CArchive 的两种方法](../mfc/two-ways-to-create-a-carchive-object.md)。

- [如何使用 CArchive <\<和 >> 运算符](../mfc/using-the-carchive-output-and-input-operators.md)。

- [存储和加载 Cobject 通过存档](../mfc/storing-and-loading-cobjects-via-an-archive.md)。

您可以让框架为您的可序列化文档创建存档或自己显式创建 `CArchive` 对象。 可以将文件和可序列化对象之间传输数据，通过使用 <\<和 >> 运算符`CArchive`或在某些情况下，通过调用`Serialize`函数的`CObject`-派生的类。

## <a name="see-also"></a>请参阅

[序列化](../mfc/serialization-in-mfc.md)
