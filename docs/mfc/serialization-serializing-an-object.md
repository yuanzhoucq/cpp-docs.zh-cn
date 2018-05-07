---
title: 序列化： 将对象序列化为 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3439857f14f4c4fa78aa2df3e3da8e5c8941938d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="serialization-serializing-an-object"></a>序列化：对象的序列化
文章[序列化： 定义可序列化类](../mfc/serialization-making-a-serializable-class.md)演示如何使类可序列化。 可序列化类之后，你可以将对象序列化为该类与通过文件的[CArchive](../mfc/reference/carchive-class.md)对象。 本文介绍：  
  
-   [CArchive 对象是](../mfc/what-is-a-carchive-object.md)。  
  
-   [创建 CArchive 的两种方式](../mfc/two-ways-to-create-a-carchive-object.md)。  
  
-   [如何使用 CArchive <\<和 >> 运算符](../mfc/using-the-carchive-output-and-input-operators.md)。  
  
-   [存储和加载 Cobject 通过存档](../mfc/storing-and-loading-cobjects-via-an-archive.md)。  
  
 您可以让框架为您的可序列化文档创建存档或自己显式创建 `CArchive` 对象。 你可以使用的数据传输的文件和可序列化对象之间 <\<和 >> 运算符`CArchive`或在某些情况下，通过调用`Serialize`函数`CObject`-派生类。  
  
## <a name="see-also"></a>请参阅  
 [序列化](../mfc/serialization-in-mfc.md)

