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
ms.openlocfilehash: da194510938e3fe02eba5993182e811fdf2e1b7c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618014"
---
# <a name="mfc-com"></a>MFC COM

MFC 子集旨在支持 COM，而大多数活动模板库（ATL）是针对 COM 编程设计的。 本节中的主题介绍 MFC 对 COM 的支持。

活动技术（如 ActiveX 控件、活动文档包含、OLE 等）使用组件对象模型（COM）使软件组件能够在网络环境中互相交互，而不考虑创建这些组件时使用的语言。 活动技术可用于创建在桌面或 Internet 上运行的应用程序。 有关详细信息，请参阅 COM 或[组件对象模型](/windows/win32/com/the-component-object-model)[简介](../atl/introduction-to-com.md)。

活动技术包括客户端和服务器技术，其中包括：

- ActiveX 控件是可以在网站等容器中使用的交互式对象。 有关 ActiveX 控件的详细信息，请参阅：

  - [MFC ActiveX 控件](mfc-activex-controls.md)

  - [Internet 上的 ActiveX 控件](activex-controls-on-the-internet.md)

  - [概述： Internet](mfc-internet-programming-basics.md)

  - [升级要在 Internet 上使用的现有 ActiveX 控件](upgrading-an-existing-activex-control.md)

  - [调试 ActiveX 控件](/visualstudio/debugger/how-to-debug-an-activex-control)

- 活动脚本控制浏览器或服务器中一个或多个 ActiveX 控件的集成行为。 有关活动脚本的详细信息，请参阅[Internet 上的活动技术](active-technology-on-the-internet.md)。

- [自动化](automation.md)（以前称为 "OLE 自动化"）使一个应用程序能够操作在其他应用程序中实现的对象，或 "公开" 对象以便可以对其进行操作。

   自动对象可能是本地或远程的（在网络上可访问的另一台计算机上）。 自动化可用于 OLE 和 COM 对象。

- 本部分还提供了有关如何使用 MFC （例如[连接点](connection-points.md)）编写 COM 组件的信息。

有关仍称为 OLE 的内容与目前称为活动技术的内容的讨论，请参阅有关[ole](ole-in-mfc.md)的主题。

## <a name="in-this-section"></a>本节内容

[活动文档包容](active-document-containment.md)

[自动化](automation.md)

[连接点](connection-points.md)

[MFC ActiveX 控件](mfc-activex-controls.md)

## <a name="see-also"></a>另请参阅

[概念](mfc-concepts.md)
