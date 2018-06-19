---
title: 文档视图创建 |Microsoft 文档
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
ms.openlocfilehash: cb89180db8e1a6cce2c40bbb4bae0965b972afa2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343518"
---
# <a name="documentview-creation"></a>文档/视图创建
框架提供的实现`New`和**打开**（及其他） 的命令上**文件**菜单。 创建新文档及其关联的视图和框架窗口是应用程序对象、 文档模板、 新建的文档和新创建的框架窗口相互合作的结果。 下表总结了哪些对象创建的内容。  
  
### <a name="object-creators"></a>对象创建者  
  
|创建者|创建|  
|-------------|-------------|  
|应用程序对象|文档模板|  
|文档模板|Document|  
|文档模板|框架窗口|  
|框架窗口|视图|  
  
## <a name="see-also"></a>请参阅  
 [文档模板和文档/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文档模板创建](../mfc/document-template-creation.md)   
 [MFC 对象之间的关系](../mfc/relationships-among-mfc-objects.md)   
 [创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)

