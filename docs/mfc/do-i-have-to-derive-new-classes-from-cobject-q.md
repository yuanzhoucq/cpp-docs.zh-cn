---
title: 我是否必须从 CObject 中派生新类？
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: 30eb3ce5bbb72ab685ed891644a478a36026ebea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352380"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>我是否必须从 CObject 中派生新类？

不，您不会。

从派生类[CObject](../mfc/reference/cobject-class.md)时所需的序列化或动态可创建性等的功能。 许多数据类需要序列化到文件中，因此，通常最好从 `CObject` 派生。 为举例说明一个类派生自`CObject`，请参阅[Scribble 示例](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>请参阅

[CObject 类：常见问题解答](../mfc/cobject-class-frequently-asked-questions.md)
