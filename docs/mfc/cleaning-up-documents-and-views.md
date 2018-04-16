---
title: "清理文档和视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a95193d5ca3df890c9c97f458b76413e588bc59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cleaning-up-documents-and-views"></a>清理文档和视图
当文档关闭时，框架将首先调用其[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)成员函数。 如果在文档操作期间分配堆上的任何内存，则 `DeleteContents` 是最佳的释放位置。  
  
> [!NOTE]
>  您不应在文档的析构函数中释放文档数据。 在 SDI 应用程序中，可能重用文档对象。  
  
 您可以重写视图的析构函数以释放在堆上分配的任何内存。  
  
## <a name="see-also"></a>请参阅  
 [初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)

