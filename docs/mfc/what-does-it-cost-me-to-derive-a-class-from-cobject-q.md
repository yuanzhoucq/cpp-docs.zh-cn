---
title: 从 CObject 派生类所带来的开销
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: 8f83bf9ee522487761aaa865a8315a174a47302d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446051"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>从 CObject 派生类所带来的开销

从[CObject](../mfc/reference/cobject-class.md)类派生的开销最小。 派生类仅继承四个虚拟函数和一个[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)对象。

## <a name="see-also"></a>另请参阅

[CObject 类：常见问题](../mfc/cobject-class-frequently-asked-questions.md)
