---
title: "创建并显示对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 109c4f2e8272293ccfcb58924380c586f8078536
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="creating-and-displaying-dialog-boxes"></a>创建并显示对话框
创建对话框对象是一个两阶段操作。 首先，构造对话框对象，然后创建对话框窗口。 模式和无模式对话框的创建和显示过程有一些不同。 下表列出了正常构造和显示模式和无模式对话框的方式。  
  
### <a name="dialog-creation"></a>对话框创建  
  
|对话框类型|如何创建|  
|-----------------|----------------------|  
|[无模式](../mfc/creating-modeless-dialog-boxes.md)|构造`CDialog`，然后调用**创建**成员函数。|  
|[模式](../mfc/creating-modal-dialog-boxes.md)|构造 `CDialog`，然后调用 `DoModal` 成员函数。|  
  
 可以如果你想创建对话框中从[内存中对话框模板](../mfc/using-a-dialog-template-in-memory.md)构造而不是从对话框模板资源。 但这是一个高级主题。  
  
## <a name="see-also"></a>另请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

