---
title: 使用 CObject
ms.date: 11/04/2016
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
ms.openlocfilehash: b5399f02819407a529fd5ec66d4f5acbb16ca002
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441925"
---
# <a name="using-cobject"></a>使用 CObject

[CObject](../mfc/reference/cobject-class.md)是大多数 Microsoft 基础类库的根基类（MFC）。 `CObject` 类包含许多有用的功能，你可能希望将这些功能合并到你自己的程序对象中，包括序列化支持、运行时类信息和对象诊断输出。 如果从 `CObject`派生类，则类可以利用这些 `CObject` 功能。

## <a name="what-do-you-want-to-do"></a>要执行的操作

- [从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)

- [将对运行时类信息、动态创建和序列化的支持添加到我的派生类](../mfc/specifying-levels-of-functionality.md)

- [访问运行时类信息](../mfc/accessing-run-time-class-information.md)

- [动态创建对象](../mfc/dynamic-object-creation.md)

- [出于诊断目的转储对象的数据](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))

- 验证对象的内部状态（请参阅[MFC ASSERT_VALID 和 CObject：： AssertValid](reference/diagnostic-services.md#assert_valid)）

- [让类自行序列化到持久存储](../mfc/serialization-in-mfc.md)

- 查看[CObject 常见问题](../mfc/cobject-class-frequently-asked-questions.md)列表

## <a name="see-also"></a>另请参阅

[概念](../mfc/mfc-concepts.md)<br/>
[常规 MFC 主题](../mfc/general-mfc-topics.md)<br/>
[CRuntimeClass 结构](../mfc/reference/cruntimeclass-structure.md)<br/>
[文件](../mfc/files-in-mfc.md)<br/>
[序列化](../mfc/serialization-in-mfc.md)
