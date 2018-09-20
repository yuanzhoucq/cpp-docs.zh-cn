---
title: OLE 后台： 链接和嵌入 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d4456e5210b2ec1e142c7ddeddd7b0e7fab9f31
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445901"
---
# <a name="ole-background-linking-and-embedding"></a>OLE 后台：链接和嵌入

在容器应用程序中使用“粘贴”命令将创建嵌入组件或嵌入项目。 嵌入项目的源数据作为包含其的 OLE 文档的一部分存储。 这样一来，字处理器文档的文档文件可包含文本，还可包含位图、图形、公式或任何其他类型的数据。

OLE 提供了另一种方式来合并其他应用程序中的数据：创建链接组件、或链接项目、或链接。 除了使用“粘贴链接”命令而不是“粘贴”命令之外，创建链接项目的步骤类似于创建嵌入项目的步骤。 与嵌入组件不同，链接组件存储到原始数据（一般位于单独的文件中）的路径。

例如，如果在字处理器文档中工作并创建一个到一些电子表格单元格的链接项目，则链接项目的数据将存储在原始电子表格文档中。 字处理器文档仅包含指定可找到项目的位置的信息，也就是说，它包含指向原始电子表格文档的链接。 当您双击单元格时，电子表格应用程序将启动，并且原始电子表格文档将从存储它的位置加载。

每个 OLE 项目，不论嵌入或链接，均基于创建其的应用程序具有与之关联的类型。 例如，Microsoft Paintbrush 项目是项目的一种类型，而 Microsoft Excel 项目是另一种类型。 但是，一些应用程序可以创建多种项目类型。 例如，Microsoft Excel 可以创建工作表项目、图表项目和宏工作表项目。 其中每个项目可以唯一标识由系统使用类标识符或**CLSID**。

## <a name="see-also"></a>请参阅

[OLE 后台](../mfc/ole-background.md)<br/>
[OLE 后台：容器和服务器](../mfc/ole-background-containers-and-servers.md)<br/>
[容器：客户端项](../mfc/containers-client-items.md)<br/>
[服务器：服务器项](../mfc/servers-server-items.md)

