---
title: "拖放： 自定义 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 387344160cf2009b19ad8de820eabc6063ae1f7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="drag-and-drop-customizing"></a>拖放：自定义
拖放功能的默认实现对大多数应用程序都够用。 但是，某些应用程序可能需要更改此标准行为。 本文说明更改这些默认设置所需的步骤。 此外，您还可以使用此方法建立不支持复合文档作为放置源的应用程序。  
  
 如果您要自定义标准 OLE 拖放行为，或者具有非 OLE 应用程序，则必须创建一个 `COleDataSource` 对象来包含该数据。 当用户启动拖放操作时，您的代码从此对象（而非支持拖放操作的其他类）应调用 `DoDragDrop` 函数。  
  
 或者，您也可以创建一个 `COleDropSource` 对象来控制放置和重写其函数，具体取决于要更改的行为的类型。 此放置源对象随后会传递给 `COleDataSource::DoDragDrop` 以更改这些函数的默认行为。 这些不同的选项在您支持应用程序中的拖放操作的方式上提供了极大的灵活性。 有关数据源的详细信息，请参阅文章[数据对象和数据源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)。  
  
 您可以重写以下函数以自定义拖放操作：  
  
|替代|以自定义|  
|--------------|------------------|  
|`OnBeginDrag`|在调用 `DoDragDrop` 后实例化拖动的方式。|  
|`GiveFeedback`|其他放置结果的可视反馈，如光标外观。|  
|`QueryContinueDrag`|拖放操作的终止。 此函数使您能够在拖动操作期间检查键修改键状态。|  
  
## <a name="see-also"></a>请参阅  
 [拖放 (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDropSource 类](../mfc/reference/coledropsource-class.md)   
 [COleDataSource 类](../mfc/reference/coledatasource-class.md)
