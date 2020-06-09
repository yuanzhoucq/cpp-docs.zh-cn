---
title: 我是否必须从 CObject 中派生新类？
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: 371ede0f0921182c066b4cb224e66b18eb6f1208
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616742"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>我是否必须从 CObject 中派生新类？

不，您不会。

当需要所提供的工具（如序列化或动态 creatability）时，从[CObject](reference/cobject-class.md)派生类。 许多数据类需要序列化到文件中，因此，通常最好从 `CObject` 派生。 有关派生自的类的示例 `CObject` ，请参阅[随意绘制的示例](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>另请参阅

[CObject 类：常见问题](cobject-class-frequently-asked-questions.md)
