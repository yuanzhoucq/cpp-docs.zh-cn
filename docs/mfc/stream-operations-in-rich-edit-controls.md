---
title: "Rich Edit 控件中的操作 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c1a73790124adbc1ff8a89290bf4e1d7a4fa6824
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="stream-operations-in-rich-edit-controls"></a>Rich Edit 控件中的流操作
你可以使用流将数据传输到或跳出 rich edit 控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 流定义通过[EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)结构，指定缓冲区和应用程序定义的回调函数。  
  
 读取数据读入格式文本编辑控件 （即，流中的数据），使用[StreamIn](../mfc/reference/cricheditctrl-class.md#streamin)成员函数。 此控件将重复调用应用程序定义的回调函数，以每次将部分数据传入缓冲区。  
  
 若要保存的内容丰富的编辑控件 （即，将数据流出），你可以使用[StreamOut](../mfc/reference/cricheditctrl-class.md#streamout)成员函数。 此控件将反复写入缓冲区，然后调用应用程序定义的回调函数。 对于每个调用，回调函数将保存缓冲区的内容。  
  
## <a name="see-also"></a>请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)

