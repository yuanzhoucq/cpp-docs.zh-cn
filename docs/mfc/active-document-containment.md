---
title: 活动文档包容
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
ms.openlocfilehash: 1c524d6890cd7b86bcae2c40d8c602e7b04e751b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623428"
---
# <a name="active-document-containment"></a>活动文档包容

活动文档包容是一种技术，它提供了用于处理文档的单个帧，而不是强制您为每个文档类型创建和使用多个应用程序框架。 它与基本 OLE 技术的不同之处在于，OLE 使用的是复合文档中的嵌入对象，其中只有一个内容可以处于活动状态。 使用活动文档包含，可以激活单个框架上下文内的整个文档（即整个应用程序，包括相关菜单、工具栏等）。

最初为实现 Office 活页夹 Microsoft Office 开发了活动文档包含技术。 不过，该技术的灵活性足以支持除 office 活页夹之外的活动文档容器，并且还可以支持除 Office 和 Office 兼容的应用程序之外的文档服务器。

承载活动文档的应用程序称为[活动文档容器](active-document-containers.md)。 此类容器的示例包括 Microsoft Office 联编程序或 Microsoft Internet Explorer。

活动文档包容作为 OLE 文档的一组扩展（OLE 的复合文档技术）实现。 扩展是附加接口，允许可嵌入的就地对象表示整个文档，而不是单个嵌入内容。 与 OLE 文档一样，活动文档包容使用为活动文档提供显示空间的容器，以及为活动文档本身提供用户界面和操作功能的服务器。

[活动文档服务器](active-document-servers.md)是支持一个或多个活动文档类的应用程序（如 Word、Excel 或 PowerPoint），其中的每个对象本身都支持允许对象在适当容器中激活的扩展接口。

[活动文档](active-documents.md)（从 Word 或 Excel 等活动文档服务器提供）实质上是一种完全缩放的传统文档，该文档在另一个活动文档容器中嵌入为一个对象。 与嵌入对象不同的是，活动文档可以完全控制其页面，并且应用程序的完整界面（及其所有基础命令和工具）可供用户编辑。

通过将活动文档与标准 OLE 嵌入对象区分开来，最能了解到活动文档。 按照 OLE 约定，嵌入对象是在拥有它的文档的页面中显示的对象，并且该文档由 OLE 容器管理。 容器将嵌入对象的数据与文档的其余部分一起存储。 但嵌入对象的限制在于它们不会控制它们所显示的页面。

活动文档容器应用程序的用户可以使用其最喜欢的应用程序（前提是启用了活动文档）来创建活动文档（已在 Office 活页夹中称为 "节"），但是用户可以将生成的项目作为单个实体进行管理，这些实体可以是唯一命名、保存、打印等的。 同样，Internet 浏览器的用户可以将整个网络（以及本地文件系统）视为单个文档存储实体，并且能够从单个位置浏览该存储中的文档。

## <a name="sample-programs"></a>示例程序

- [MFCBIND](../overview/visual-cpp-samples.md)示例演示了如何实现活动文档容器应用程序。

## <a name="see-also"></a>另请参阅

[MFC COM](mfc-com.md)
