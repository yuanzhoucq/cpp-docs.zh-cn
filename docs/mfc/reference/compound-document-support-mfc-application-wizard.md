---
title: 复合文档支持，MFC 应用程序向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.compdoc
dev_langs:
- C++
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fef6fd59166a0999221d420f58e0f329c780fd06
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416066"
---
# <a name="compound-document-support-mfc-application-wizard"></a>MFC 应用程序向导的复合文档支持

在 MFC 应用程序向导的此页上，指示你的应用程序提供的复合活动的文档支持级别。 你的应用程序必须支持文档/视图体系结构来支持复合文档和文档模板。

默认情况下，应用程序包含不支持复合文档。 如果你接受此默认设置，你的应用程序不能支持活动文档或复合文件。

- **复合文档支持**

   确定你的应用程序提供了容器支持、 服务器支持，或两者。 有关这方面的详细信息，请参阅：

   - [容器：实现容器](../../mfc/containers-implementing-a-container.md)

   - [服务器：实现服务器](../../mfc/servers-implementing-a-server.md)

   |选项|描述|
   |------------|-----------------|
   |**无**|指示不支持对象链接和嵌入 (OLE)。 默认情况下，应用程序向导创建没有 ActiveX 支持的应用程序。|
   |**容器**|包含链接和嵌入对象。|
   |**袖珍服务器**|指示应用程序可以创建和管理复合文档对象。 请注意，不能运行袖珍服务器独立运行且只支持嵌入的项。|
   |**完整的服务器**|指示应用程序可以创建和管理复合文档对象。 完整的服务器都能够运行独立和支持同时链接和嵌入的项。|
   |**容器/完全服务器**|指示应用程序可以为容器和服务器。 容器是可以嵌入或链接项并入自己的文档的应用程序。 服务器是可以创建供容器应用程序使用的自动化项的应用程序。|

- **附加选项**

   指示您的应用程序是否支持活动文档。 请参阅[活动文档](../../mfc/active-documents.md)有关此功能的详细信息。

   |选项|描述|
   |------------|-----------------|
   |**活动文档服务器**|指示应用程序可以创建和管理活动文档。 如果选择此选项，必须为活动文档服务器中指定的文件扩展名**文件扩展名**框中[文档模板字符串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)向导页。 请参阅[活动文档服务器](../../mfc/active-document-servers.md)有关详细信息。|
   |**活动文档容器**|指示应用程序可以包含其范围内的活动文档。 例如，Internet Explorer 文档或 Office 文档，如 Microsoft Word 文件或 Excel 电子表格，可能包括活动文档。 请参阅[活动文档包容](../../mfc/active-document-containment.md)有关详细信息。|
   |**对复合文件的支持**|使用复合文件格式的容器应用程序的文档不会进行序列化。 此选项将强制加载到内存中包含的对象的整个文件。 为单个对象的增量存储不可用。 如果一个对象已更改，并且随后保存，然后保存该文件中的所有对象。|

## <a name="see-also"></a>请参阅

[MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)

