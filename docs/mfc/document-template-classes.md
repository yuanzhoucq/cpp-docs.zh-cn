---
title: 文档模板类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 2589bc8f04e791f73529af91ffb148c2c717cd08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164977"
---
# <a name="document-template-classes"></a>文档模板类

文档模板对象协调的文档、 视图和框架窗口对象的新文档时创建，或创建视图。

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
文档模板的基类。 您不应直接; 使用此类相反，使用此类派生的其他文档模板类中。

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
多文档的界面 (MDI) 中的文档的模板。 MDI 应用程序可以有一次打开多个文档。

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
对于单文档界面 (SDI) 中的文档模板。 SDI 应用程序具有仅一次打开文档。

## <a name="related-class"></a>相关的类

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
一种结构的文档模板传递给窗口创建函数来协调文档、 视图和框架窗口对象的创建。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)
