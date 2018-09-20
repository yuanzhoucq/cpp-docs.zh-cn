---
title: 我是否必须从 CObject 中派生新类？ | Microsoft Docs
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
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec080e556b57afadbc3d958f4dba5ac6393108aa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408903"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>我是否必须从 CObject 中派生新类？

不，您不会。

从派生类[CObject](../mfc/reference/cobject-class.md)时所需的序列化或动态可创建性等的功能。 许多数据类需要序列化到文件中，因此，通常最好从 `CObject` 派生。 为举例说明一个类派生自`CObject`，请参阅[Scribble 示例](../visual-cpp-samples.md)。

## <a name="see-also"></a>请参阅

[CObject 类：常见问题](../mfc/cobject-class-frequently-asked-questions.md)
