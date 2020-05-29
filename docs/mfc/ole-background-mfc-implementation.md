---
title: OLE 后台：MFC 实现
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
ms.openlocfilehash: 25c98c3683a8656bb5188f22d0464d25a4901f49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364534"
---
# <a name="ole-background-mfc-implementation"></a>OLE 后台：MFC 实现

由于原始 OLE API 的大小和复杂性，直接调用它来编写 OLE 应用程序会非常耗时。 OLE 的 Microsoft 基础类库实现的目的是减少编写功能齐全、具有 OLE 功能的应用程序所必须进行的工作量。

本文将介绍 MFC 中尚未实现的部分 OLE API。 讨论还解释了实现的内容如何映射到 Windows SDK 的 OLE 部分。

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>类库未实现的 OLE 部分

MFC 未直接提供 OLE 的一些接口和功能。 如果您要使用这些功能，可以直接调用 OLE API。

IMoniker 接口`IMoniker`接口由类库（例如类）实现，`COleServerItem`但以前未向程序员公开。 有关此接口的详细信息，请参阅 Windows SDK OLE 部分中的 OLE Moniker 实现。 但是，请参阅类[CMonikerFile](../mfc/reference/cmonikerfile-class.md)和[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)。

I未知接口和 IMarshal`IUnknown`接口 接口由类库实现，但不向程序员公开。 接口`IMarshal`不是由类库实现的，而是内部使用的。 使用类库生成的自动化服务器已内置了封送功能。

类库部分支持文档文件（复合文件）复合文件。 任何直接操作复合文件的函数（创建复合文件的函数除外）都不受支持。 MFC 使用`COleFileStream`类支持使用标准文件函数的流进行操作。 有关详细信息，请参阅文章[容器：复合文件](../mfc/containers-compound-files.md)。

进程内服务器和对象处理程序 进程中的服务器和对象处理程序允许在动态链接库 （DLL） 中实现可视化编辑数据或完整的组件对象模型 （COM） 对象。 为此，可以通过直接调用 OLE API 实现 DLL。 但是，如果您正在编写自动化服务器而且该服务器没有用户界面，则可使用 AppWizard 使该服务器成为进程内服务器并将其完全置于 DLL 中。 有关这些主题的详细信息，请参阅[自动化服务器](../mfc/automation-servers.md)。

> [!TIP]
> 实现自动化服务器的最简单方法是将它置于 DLL 中。 MFC 支持这种做法。

有关 Microsoft 基础 OLE 类如何实现 OLE 接口的详细信息，请参阅 MFC 技术说明[38、39](../mfc/tn038-mfc-ole-iunknown-implementation.md)和[40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。 [39](../mfc/tn039-mfc-ole-automation-implementation.md)

## <a name="see-also"></a>另请参阅

[OLE 背景](../mfc/ole-background.md)<br/>
[OLE 后台：实现策略](../mfc/ole-background-implementation-strategies.md)
