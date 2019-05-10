---
title: 文档-视图创建
ms.date: 11/04/2016
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
ms.openlocfilehash: b5f9b783e8e14744a816fd63b327ed95d9da8e8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240776"
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
