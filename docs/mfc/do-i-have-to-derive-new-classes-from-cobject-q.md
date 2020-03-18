---
title: 我是否必须从 CObject 中派生新类？
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: d38e589f371fc56f5566c56de7b19c366065a503
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446922"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>我是否必须从 CObject 中派生新类？

不，您不会。

当需要所提供的工具（如序列化或动态 creatability）时，从[CObject](../mfc/reference/cobject-class.md)派生类。 许多数据类需要序列化到文件中，因此，通常最好从 `CObject` 派生。 有关从 `CObject`派生的类的示例，请参阅[随意绘制的示例](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>另请参阅

[CObject 类：常见问题](../mfc/cobject-class-frequently-asked-questions.md)
