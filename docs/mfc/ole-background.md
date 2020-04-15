---
title: OLE 后台
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: f7d65f48c1af678f6626ba7d315ceb735d3e960a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364523"
---
# <a name="ole-background"></a>OLE 后台

OLE 是一个机制，用来支持用户创建和编辑包含由多个应用程序创建的项或“对象”的文档。

> [!NOTE]
> OLE 最初是对象链接和嵌入 (Object Linking and Embedding) 的首字母缩写。 但是，它现在称为“OLE”。 部分与链接和嵌入不相关的 OLE 现在是 Active 技术的一部分。

OLE 文档（以前称为复合文档）可与各种类型的数据或组件无缝集成。 声音剪辑、电子表格和位图是 OLE 文档中典型的组件示例。 通过在应用程序中支持 OLE，用户可以使用 OLE 文档而不用为在不同的应用程序之间切换烦恼；OLE 将为您执行该切换。

您可使用容器应用程序创建复合文档，还可使用服务器应用程序或组件应用程序创建容器文档中的项。 您编写的任何应用程序都可以是容器、服务器或兼具这两种类型。

OLE 包含很多不同的概念，它们全部用于实现应用程序之间的无缝集成。 这些概念包括：

- 链接和嵌入

   链接和嵌入是两种用于存储创建于 OLE 文档（在其他应用程序中创建）中的项的方法。 有关两者差异的一般信息，请参阅文章[OLE 背景：链接和嵌入](../mfc/ole-background-linking-and-embedding.md)。 有关详细信息，请参阅[容器](../mfc/containers.md)和[服务器](../mfc/servers.md)的文章。

- 就地激活（可视化编辑）

   在容器文档的上下文中激活嵌入项称为就地激活或可视化编辑。 容器应用程序的接口将更改以包含创建嵌入项的组件应用程序的功能。 链接项绝不会就地激活，因为该项的实际数据包含在单独的文件中，位于包含该链接的应用程序的上下文之外。 有关就地激活的详细信息，请参阅文章["激活](../mfc/activation-cpp.md)"。

   > [!NOTE]
   > 链接与嵌入和就地激活提供了 OLE 可视化编辑的主要功能。

- 自动化自动化允许一个应用程序驱动另一个应用程序。 执行驱动的应用程序称为自动化客户端，被驱动的应用程序称为自动化服务器或自动化组件。 有关自动化的详细信息，请参阅[文章"自动化客户端](../mfc/automation-clients.md)"和"[自动化服务器](../mfc/automation-servers.md)"。

   > [!NOTE]
   > 自动化可在 OLE 和 Active 技术上下文中工作。 您可以自动化基于 COM 的任何对象。

- 复合文件

   复合文件提供了一个标准文件格式，用于简化 OLE 应用程序的复合文档的结构化存储。 在复合文件中，存储具有目录的很多功能，而流具有文件的很多功能。 此技术也称为结构化存储。 有关复合文件的详细信息，请参阅文章[容器：复合文件](../mfc/containers-compound-files.md)。

- 统一数据传输

   统一数据传输 (UDT) 是一组接口，用于支持以标准方式发送和接收数据（无论选择的传输数据的实际方法如何）。 UDT 为通过拖放进行数据传输奠定了基础。 UDT 现在充当现有 Windows 数据传输（如剪贴板和动态数据交换 (DDE)）的基础。 有关 UDT 的详细信息，请参阅文章["数据对象和数据源 （OLE）"。](../mfc/data-objects-and-data-sources-ole.md)

- 拖放

   拖放是一种易于使用的直接操作技术，可用于在多个应用程序之间、在一个应用程序的多个窗口之间甚至是在一个应用程序中的单个窗口中传输数据。 您可选择要传输的数据并将其拖到所需的目标。 拖放基于统一数据传输。 有关拖放的详细信息，请参阅文章["拖放](../mfc/drag-and-drop-ole.md)"。

- 组件对象模型 (Component Object Model)

   组件对象模型 (COM) 提供了 OLE 对象互相通信时使用的基础结构。 MFC OLE 类为程序员简化了 COM。 COM 是 Active 技术的一部分，因为 COM 对象以 OLE 和 Active 技术为基础。 有关 COM 的详细信息，请参阅[活动模板库 （ATL）](../atl/active-template-library-atl-concepts.md)主题。

一些更重要的 OLE 主题包含在以下文章中：

- [OLE 后台：链接和嵌入](../mfc/ole-background-linking-and-embedding.md)

- [OLE 后台：容器和服务器](../mfc/ole-background-containers-and-servers.md)

- [OLE 后台：实现策略](../mfc/ole-background-implementation-strategies.md)

- [OLE 后台：MFC 实现](../mfc/ole-background-mfc-implementation.md)

对于上述文章中找不到的常规 OLE 信息，请在 MSDN 中搜索 OLE。

## <a name="see-also"></a>另请参阅

[OLE](../mfc/ole-in-mfc.md)
