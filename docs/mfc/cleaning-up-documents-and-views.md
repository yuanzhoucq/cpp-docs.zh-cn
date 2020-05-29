---
title: 清理文档和视图
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 06ff60a2cf6245f64e80d899c13a8444558fcf0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374624"
---
# <a name="cleaning-up-documents-and-views"></a>清理文档和视图

当文档关闭时，框架首先调用其[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)成员函数。 如果在文档操作期间分配堆上的任何内存，则 `DeleteContents` 是最佳的释放位置。

> [!NOTE]
> 您不应在文档的析构函数中释放文档数据。 在 SDI 应用程序中，可能重用文档对象。

您可以重写视图的析构函数以释放在堆上分配的任何内存。

## <a name="see-also"></a>另请参阅

[初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)
