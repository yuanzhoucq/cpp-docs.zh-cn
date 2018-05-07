---
title: 从 CObject 派生类所带来的开销 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffff35cdef6cf2f730687334bbb56bc078371a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>从 CObject 派生类所带来的开销
从类派生的系统开销[CObject](../mfc/reference/cobject-class.md)很小。 在派生的类继承，只需四个虚函数，只要有一个[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)对象。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类：常见问题](../mfc/cobject-class-frequently-asked-questions.md)
