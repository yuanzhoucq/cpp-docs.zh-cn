---
title: 文档模板创建
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
ms.openlocfilehash: 85ff6ad47b37d85c812608dbee918f0543730eae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219803"
---
# <a name="document-template-creation"></a>文档模板创建

在响应中创建一个新文档时**新建**或**打开**命令**文件**菜单中，文档模板还创建用来查看新的框架窗口文档。

文档模板构造函数指定哪些类型的文档、 窗口和视图将能够创建模板。 这是通过将传递给文档模板构造函数的参数确定的。 下面的代码演示创建[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)示例应用程序：

[!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]

指向新指针`CMultiDocTemplate`使用对象作为参数[AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate)。 自变量`CMultiDocTemplate`构造函数包含文档类型的菜单和快捷键，与关联的资源 ID 和三个用途[RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)宏。 `RUNTIME_CLASS` 返回[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)对象的C++作为其参数名为的类。 这三个`CRuntimeClass`对象传递给文档模板构造函数提供文档创建过程中创建的指定类的新对象所需的信息。 该示例演示如何创建用于创建的文档模板`CScribDoc`对象与`CScribView`附加的对象。 视图是构建框架通过标准的 MDI 子框架窗口。

## <a name="see-also"></a>请参阅

[文档模板和文档/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[文档/视图创建](../mfc/document-view-creation.md)<br/>
[MFC 对象之间的关系](../mfc/relationships-among-mfc-objects.md)<br/>
[创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)
