---
title: 使用 CObject |Microsoft Docs
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
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f421624f16a11f02dc260ce95a9d2cf11fcd9fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399127"
---
# <a name="using-cobject"></a>使用 CObject

[CObject](../mfc/reference/cobject-class.md)对于大多数的 Microsoft 基础类库 (MFC) 是根的基类。 `CObject`类包含许多有用的功能，您可能想要合并到您自己的程序对象，包括序列化支持、 运行时类信息，以及诊断输出对象。 如果派生您的类从`CObject`，你的类可以利用这些`CObject`功能。

## <a name="what-do-you-want-to-do"></a>你想要做什么

- [从 CObject 中派生一个类](../mfc/deriving-a-class-from-cobject.md)

- [将对运行时类信息、 动态创建和序列化的支持添加到我的派生类](../mfc/specifying-levels-of-functionality.md)

- [访问运行时类信息](../mfc/accessing-run-time-class-information.md)

- [动态创建对象](../mfc/dynamic-object-creation.md)

- [对象的数据转储以进行诊断](/previous-versions/visualstudio/visual-studio-2010/sc15kz85\(v=vs.100\))

- 验证对象的内部状态 (请参阅[MFC ASSERT_VALID 和 CObject::AssertValid](reference/diagnostic-services.md#assert_valid))

- [类将自行序列化到持久存储](../mfc/serialization-in-mfc.md)

- 查看一系列[CObject 常见问题](../mfc/cobject-class-frequently-asked-questions.md)

## <a name="see-also"></a>请参阅

[概念](../mfc/mfc-concepts.md)<br/>
[常规 MFC 主题](../mfc/general-mfc-topics.md)<br/>
[CRuntimeClass 结构](../mfc/reference/cruntimeclass-structure.md)<br/>
[文件](../mfc/files-in-mfc.md)<br/>
[序列化](../mfc/serialization-in-mfc.md)

