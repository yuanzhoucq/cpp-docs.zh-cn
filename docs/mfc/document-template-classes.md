---
title: 文档模板类
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 82b9ce4c242df7c85ada0722b2c1e993a0cf3f81
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446911"
---
# <a name="document-template-classes"></a>文档模板类

创建新文档或视图时，文档模板对象协调文档、视图和框架窗口对象的创建。

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
文档模板的基类。 永远不会直接使用此类;而是使用派生自此类的其他文档模板类之一。

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
多文档界面（MDI）中文档的模板。 MDI 应用程序一次可以打开多个文档。

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
单文档界面（SDI）的文档模板。 SDI 应用程序一次只能打开一个文档。

## <a name="related-class"></a>相关类

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
文档模板传递给窗口创建函数的结构，用来协调文档、视图和框架窗口对象的创建。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
