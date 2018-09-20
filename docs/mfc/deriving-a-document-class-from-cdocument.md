---
title: 从 CDocument 派生文档类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b45dadbc062bbba61cdcb4c883f91943b1b18ba8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429820"
---
# <a name="deriving-a-document-class-from-cdocument"></a>从 CDocument 派生文档类

文档包含和管理应用程序的数据。 若要使用的 MFC 应用程序向导提供的文档类，必须执行以下操作：

- 从派生类`CDocument`每种类型的文档。

- 添加成员变量来存储每个文档的数据。

- 重写`CDocument`的`Serialize`成员函数在您的文档类。 `Serialize` 写入，并读取文档的数据传入和传出磁盘。

## <a name="other-document-functions-often-overridden"></a>经常重写其他文档函数

您可能还想要重写其他`CDocument`成员函数。 具体而言，通常将需要重写[OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)并[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)文档的数据成员进行初始化并[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)销毁动态分配的数据。 可重写成员的信息，请参阅类[CDocument](../mfc/reference/cdocument-class.md)中*MFC 参考*。

## <a name="see-also"></a>请参阅

[使用文档](../mfc/using-documents.md)

