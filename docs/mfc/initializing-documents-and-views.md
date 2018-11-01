---
title: 初始化文档和视图
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: 2fb557d55576678d8c1199bec20e1fa4c849e1b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612246"
---
# <a name="initializing-documents-and-views"></a>初始化文档和视图

文档以两种不同的方式创建，因此您的文档类必须支持这两种方式。 第一种方式，用户可以使用“文件”->“新建”命令创建一个新的空白文档。 在这种情况下，初始化此文档中的重写[OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)类的成员函数[CDocument](../mfc/reference/cdocument-class.md)。 第二种方式，用户可以使用“文件”菜单上的“打开”命令来创建一个内容读取自某个文件的新文档。 在这种情况下，初始化此文档中的重写[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)类的成员函数`CDocument`。 如果两个初始化操作相同，则可以从这两个重写中调用一个公用成员函数，或者 `OnOpenDocument` 可以调用 `OnNewDocument` 来初始化一个干净的文档，然后完成打开操作。

创建文档之后，将创建视图。 初始化视图的最佳时机是在框架创建完文档、框架窗口和视图之后。 可以通过重写中初始化您的视图[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)成员函数[CView](../mfc/reference/cview-class.md)。 如果您需要重新初始化或调整任何内容每次文档发生更改时，您可以重写[OnUpdate](../mfc/reference/cview-class.md#onupdate)。

## <a name="see-also"></a>请参阅

[初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)

