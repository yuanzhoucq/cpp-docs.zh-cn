---
title: 用于创建 OLE 应用程序的操作顺序
ms.date: 11/04/2016
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
ms.openlocfilehash: b7fa989d1a3b799cf6b427e27142d4479be900bf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263567"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>用于创建 OLE 应用程序的操作顺序

下表显示了创建 OLE 链接和嵌入应用程序角色和框架的角色。 这些表示可用的选项而不是序列的步骤执行。

### <a name="creating-ole-applications"></a>创建 OLE 应用程序

|任务|您执行的操作|框架执行的操作|
|----------|------------|------------------------|
|创建 COM 组件。|运行 MFC 应用程序向导。 选择**完全服务器**或**袖珍服务器**中**复合文档支持**选项卡。|框架生成主干应用程序与 COM 组件功能已启用。 所有的 COM 功能可以传输到仅稍加修改与现有的应用程序。|
|从头开始创建容器应用程序。|运行 MFC 应用程序向导。 选择**容器**中**复合文档支持**选项卡。使用类视图，转到源代码编辑器。 填写 COM 处理程序函数的代码。|框架生成主干应用程序，可以将其插入所创建的 COM 组件 （服务器） 应用程序的 COM 对象。|
|创建一个从零开始支持自动化应用程序。|运行 MFC 应用程序向导。 选择**自动化**从**高级功能**选项卡。使用类视图公开方法和自动化应用程序中的属性。|框架生成主干应用程序，可以激活和其他应用程序可以自动完成。|

## <a name="see-also"></a>请参阅

[基于框架生成](../mfc/building-on-the-framework.md)<br/>
[MFC 应用程序的构建操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[ActiveX 控件的创建操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[数据库应用程序的创建操作顺序](../mfc/sequence-of-operations-for-creating-database-applications.md)
