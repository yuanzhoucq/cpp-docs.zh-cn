---
title: 文档-视图创建 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], creating
- views [MFC], and frame windows
- views [MFC], creating
- tables [MFC]
- MFC, views
- document/view architecture [MFC], creating document/view
- object creators
- MFC, documents
- tables [MFC], objects each MFC object creates
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0deb187a6540af71a1dc72b730347374bc25f963
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423048"
---
# <a name="documentview-creation"></a>文档/视图创建

该框架提供的实现**新建**并**打开**（及其他） 上的命令**文件**菜单。 创建一个新文档及其关联的视图和框架窗口是在应用程序对象、 文档模板、 新建的文档和新创建的框架窗口之间协作的成果。 下表总结了哪些对象创建的内容。

### <a name="object-creators"></a>对象创建器

|创建者|创建|
|-------------|-------------|
|应用程序对象|文档模板|
|文档模板|Document|
|文档模板|框架窗口|
|框架窗口|视图|

## <a name="see-also"></a>请参阅

[文档模板和文档/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[文档模板创建](../mfc/document-template-creation.md)<br/>
[MFC 对象之间的关系](../mfc/relationships-among-mfc-objects.md)<br/>
[创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)

