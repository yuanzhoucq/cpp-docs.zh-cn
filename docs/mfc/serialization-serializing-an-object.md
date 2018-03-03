---
title: "序列化： 将对象序列化为 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37e688a3619cd203e61997999a9b7eb7651d73fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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

