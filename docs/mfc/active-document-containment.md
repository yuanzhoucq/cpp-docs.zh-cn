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
ms.openlocfilehash: dc13384454c4732d3efbf99def5d05dd4f2d44aa
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776565"
---
# <a name="active-document-containment"></a>活动文档包容

活动文档包容是一种技术，提供了一个框架，用于处理的文档，而不是强制您将创建并对每个文档类型使用多个应用程序框架。 它与基本 OLE 技术的 OLE 适用于在复合文档只有一段内容可以处于活动状态的嵌入对象。 使用活动文档包容单个帧的上下文中激活整个文档 （即，整个应用程序，包括关联的菜单、 工具栏和等等）。

活动文档包容技术最初是针对 Microsoft Office 来实现 Office 活页夹开发的。 但是，技术的灵活程度足以支持非 Office 活页夹的活动文档容器，并且可以支持 Office 和 Office 兼容的应用程序以外的文档服务器。

承载活动文档的应用程序称为[活动文档容器](../mfc/active-document-containers.md)。 此类容器的示例包括 Microsoft Office Binder 或 Microsoft Internet Explorer。

作为一组扩展到 OLE 文档、 OLE 的复合文档技术，被实现活动文档包容。 扩展是允许可嵌入、 就地对象表示整个文档而不是单个片段嵌入内容的其他接口。 与 OLE 文档一样活动文档包容使用提供的活动文档中和为在活动文档中自行提供用户界面和操作功能的服务器的显示空间的容器。

[活动文档服务器](../mfc/active-document-servers.md)是支持一个或多个活动文档类 （如 Word、 Excel 或 PowerPoint） 的应用程序，其中每个对象本身支持允许要在激活的对象的扩展插件接口适用的容器。

[活动文档](../mfc/active-documents.md)（提供从活动文档服务器如 Word 或 Excel） 实质上是一个全面的常规文档，将嵌入为另一个活动文档容器中的对象。 与嵌入对象不同的活动文档可以完全控制其页面和应用程序 （具有所有其底层命令和工具） 的完整接口可供用户对其进行编辑。

活动文档最清楚地了解区分与标准的 OLE 嵌入对象。 按照 OLE 约定，嵌入的对象是一个显示在拥有它，文档的页内和文档由 OLE 容器。 容器存储文档的其余部分使用的嵌入的对象的数据。 但是，嵌入的对象是有限的他们不控制它们会显示的页。

活动文档容器应用程序的用户可以创建活动文档 （称为 Office 活页夹中的部分） （只要这些应用程序支持活动文档） 使用他们喜欢的应用程序，但用户可以管理作为生成的项目单个实体，可唯一地命名为，保存，打印，依次类推。 同样地，在 Internet 浏览器的用户可以视为整个网络，以及本地文件系统，能够浏览该存储从一个位置中的文档的单个文档存储实体。

## <a name="sample-programs"></a>示例程序

- [MFCBIND](../overview/visual-cpp-samples.md)示例说明了活动文档容器应用程序的实现。

## <a name="see-also"></a>请参阅

[MFC COM](../mfc/mfc-com.md)
