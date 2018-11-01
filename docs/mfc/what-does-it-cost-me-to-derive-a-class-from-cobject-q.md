---
title: 从 CObject 派生类所带来的开销
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: 521b6a32e3e5b34b4da9dab3117d55a728bd8e88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500440"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>从 CObject 派生类所带来的开销

从类派生的开销[CObject](../mfc/reference/cobject-class.md)很小。 在派生的类继承，只需四个虚函数，只要有一个[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)对象。

## <a name="see-also"></a>请参阅

[CObject 类：常见问题](../mfc/cobject-class-frequently-asked-questions.md)
