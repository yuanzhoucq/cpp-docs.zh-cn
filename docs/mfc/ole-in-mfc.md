---
title: MFC 中的 OLE
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
ms.openlocfilehash: 529b6d0eaedaee200da547ef9ed980aab51ea233
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622177"
---
# <a name="ole-in-mfc"></a>MFC 中的 OLE

本文介绍使用 MFC 进行 OLE 编程的基础知识。 MFC 提供了写入使用 OLE 的程序的最简单的方法：

- 使用 OLE 可视编辑（就地激活）。

- 像 OLE 容器或服务器一样工作。

- 实现拖放功能。

- 使用日期和时间数据。

- 管理 MFC 模块的状态数据，包括导出的 DLL 函数入口点，OLE/COM 接口入口点和窗口过程入口点。

你还可以使用[自动化](automation.md)。

> [!NOTE]
> OLE 一词表示与链接和嵌入关联的技术，包括 OLE 容器、OLE 服务器、OLE 项、就地激活（也称为可视编辑）跟踪器、拖放和菜单合并。 Active 一词适用于组件对象模型 (COM) 和基于 COM 的对象（如 ActiveX 控件）。 OLE 自动化现在称为自动化。

## <a name="in-this-section"></a>本节内容

[OLE 背景](ole-background.md)<br/>
讨论 OLE 并提供有关它的工作原理的概念性信息。

[激活](activation-cpp.md)<br/>
说明激活在编辑 OLE 项中的作用。

[容器](containers.md)<br/>
提供有关在 OLE 中使用容器的链接。

[数据对象和数据源](data-objects-and-data-sources-ole.md)<br/>
提供指向讨论 `COleDataObject` 和 `COleDataSource` 类的使用的主题的链接。

[拖放](drag-and-drop-ole.md)<br/>
讨论如何对 OLE 使用复制和粘贴

[OLE 菜单和资源](menus-and-resources-ole.md)<br/>
说明菜单和资源在 MFC OLE 文档应用程序中的使用。

[注册](registration.md)<br/>
讨论服务器安装和初始化。

[服务器](servers.md)<br/>
介绍如何创建供容器应用程序使用的 OLE 项（或组件）。

[跟踪](trackers.md)<br/>
提供有关 `CRectTracker` 类的信息，该类提供了一个供用户与 OLE 客户端项交互的图形界面。

## <a name="related-sections"></a>相关章节

[连接点](connection-points.md)<br/>
介绍如何使用 MFC 类、`CCmdTarget` 和 `CConnectionPoint` 实现连接点（以前称为 OLE 连接点）。

[容器/服务器 COM 组件](containers-advanced-features.md)<br/>
介绍将可选高级功能合并到现有容器应用程序中所需的步骤。

[组件对象模型](/windows/win32/com/the-component-object-model)<br/>
介绍如何在没有 MFC 的情况下使用 OLE。

## <a name="see-also"></a>另请参阅

[概念](mfc-concepts.md)
