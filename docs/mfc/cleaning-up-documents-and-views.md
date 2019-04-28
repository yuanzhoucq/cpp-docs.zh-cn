---
title: 清理文档和视图
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 940c768823d26950d9710fb1d1a52e6a1955fead
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327153"
---
# <a name="cleaning-up-documents-and-views"></a>清理文档和视图

关闭文档后，框架首先将调用其[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)成员函数。 如果在文档操作期间分配堆上的任何内存，则 `DeleteContents` 是最佳的释放位置。

> [!NOTE]
>  您不应在文档的析构函数中释放文档数据。 在 SDI 应用程序中，可能重用文档对象。

您可以重写视图的析构函数以释放在堆上分配的任何内存。

## <a name="see-also"></a>请参阅

[初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)
