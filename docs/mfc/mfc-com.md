---
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: 514251475050e728be1959417ead1dbdf96e4800
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358205"
---
# <a name="mfc-com"></a>MFC COM

MFC 的子集旨在支持 COM，而大多数活动模板库 （ATL） 专为 COM 编程而设计。 本部分主题介绍了 MFC 对 COM 的支持。

活动技术（如 ActiveX 控件、活动文档包含、OLE 等）使用组件对象模型 （COM） 使软件组件能够在网络环境中相互交互，而不管它们使用何种语言。 活动技术可用于创建在桌面或 Internet 上运行的应用程序。 有关详细信息，请参阅[COM 或](../atl/introduction-to-com.md)[组件对象模型](/windows/win32/com/the-component-object-model)简介。

活动技术包括客户端和服务器技术，包括：

- ActiveX 控件是交互式对象，可用于容器（如网站）。 有关 ActiveX 控件的详细信息，请参阅：

  - [MFC 活动X控制](../mfc/mfc-activex-controls.md)

  - [互联网上的 ActiveX 控制](../mfc/activex-controls-on-the-internet.md)

  - [概述：互联网](../mfc/mfc-internet-programming-basics.md)

  - [升级要在 Internet 上使用的现有 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)

  - [调试 ActiveX 控件](/visualstudio/debugger/how-to-debug-an-activex-control)

- 活动脚本控制浏览器或服务器中一个或多个 ActiveX 控件的集成行为。 有关活动脚本的详细信息，请参阅 Internet[上的活动技术](../mfc/active-technology-on-the-internet.md)。

- [自动化](../mfc/automation.md)（以前称为 OLE 自动化）使一个应用程序能够操作在另一个应用程序中实现的对象，或者"公开"对象，以便可以对其进行操作。

   自动对象可能是本地的或远程的（在通过网络可访问的另一台计算机上）。 自动化可用于 OLE 和 COM 对象。

- 本节还提供有关如何使用 MFC 写入 COM 组件的信息，例如，在[连接点](../mfc/connection-points.md)中。

有关仍称为 OLE 与现在称为活动技术的讨论，请参阅[OLE](../mfc/ole-in-mfc.md)上的主题。

## <a name="in-this-section"></a>本节内容

[活动文档包含](../mfc/active-document-containment.md)

[自动化](../mfc/automation.md)

[连接点](../mfc/connection-points.md)

[MFC 活动X控制](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>另请参阅

[概念](../mfc/mfc-concepts.md)
