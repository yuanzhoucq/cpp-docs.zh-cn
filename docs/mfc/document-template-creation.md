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
ms.openlocfilehash: 952a383792eb3a4d0a4ed1b3e24dd82f7fa644cf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615784"
---
# <a name="document-template-creation"></a>文档模板创建

当在 "**文件**" 菜单中创建新文档来响应**新**的或**打开**的命令时，文档模板还将创建一个新的框架窗口，通过该窗口查看文档。

文档模板构造函数指定模板可以创建的文档、窗口和视图的类型。 这取决于您传递给文档模板构造函数的参数。 下面的代码演示如何为示例应用程序创建[CMultiDocTemplate](reference/cmultidoctemplate-class.md) ：

[!code-cpp[NVC_MFCDocView#7](codesnippet/cpp/document-template-creation_1.cpp)]

指向新对象的指针用作 `CMultiDocTemplate` [AddDocTemplate](reference/cwinapp-class.md#adddoctemplate)的参数。 `CMultiDocTemplate`构造函数的参数包括与文档类型的菜单和快捷键相关联的资源 ID，以及三个[RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class)宏的用法。 `RUNTIME_CLASS`返回名为的 c + + 类的[CRuntimeClass](reference/cruntimeclass-structure.md)对象作为其参数。 `CRuntimeClass`传递给文档模板构造函数的三个对象提供在文档创建过程中创建指定类的新对象所需的信息。 该示例演示如何创建一个文档模板，该模板创建对象 `CScribDoc` 并 `CScribView` 附加了对象。 视图通过标准 MDI 子框架窗口进行分帧。

## <a name="see-also"></a>另请参阅

[文档模板和文档/视图创建过程](document-templates-and-the-document-view-creation-process.md)<br/>
[文档/视图创建](document-view-creation.md)<br/>
[MFC 对象之间的关系](relationships-among-mfc-objects.md)<br/>
[创建新文档、窗口和视图](creating-new-documents-windows-and-views.md)
