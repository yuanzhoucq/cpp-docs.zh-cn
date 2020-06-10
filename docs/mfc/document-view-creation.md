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
ms.openlocfilehash: 5441827188f5bff98638cc85cd29e2efd79f8ae8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620345"
---
# <a name="documentview-creation"></a>文档/视图创建

框架提供 "**文件**" 菜单上的**新**的和**打开**的命令的实现。 在应用程序对象、文档模板、新创建的文档和新创建的框架窗口中，创建新文档及其关联的视图和框架窗口是一项协作工作。 下表总结了哪些对象创建了什么。

### <a name="object-creators"></a>对象创建者

|创建者|创建|
|-------------|-------------|
|应用程序对象|文档模板|
|文档模板|文档|
|文档模板|框架窗口|
|框架窗口|视图|

## <a name="see-also"></a>另请参阅

[文档模板和文档/视图创建过程](document-templates-and-the-document-view-creation-process.md)<br/>
[文档模板创建](document-template-creation.md)<br/>
[MFC 对象之间的关系](relationships-among-mfc-objects.md)<br/>
[创建新文档、窗口和视图](creating-new-documents-windows-and-views.md)
