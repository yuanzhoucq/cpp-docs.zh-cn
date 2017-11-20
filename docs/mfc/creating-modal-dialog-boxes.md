---
title: "创建模式对话框 |Microsoft 文档"
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
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 662455a3ad0c45b287f485e3b87cc5437343bffb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="creating-modal-dialog-boxes"></a>创建模式对话框
若要创建模式对话框，请调用中声明的两个公共构造函数之一[CDialog](../mfc/reference/cdialog-class.md)。 接下来，调用对话框对象的[DoModal](../mfc/reference/cdialog-class.md#domodal)成员函数以显示对话框中和管理与之交互，直到用户选择确定或取消。 正是由 `DoModal` 进行的上述管理工作使得对话框成为模式对话框。 对于模式对话框，`DoModal` 将加载对话框资源。  
  
## <a name="see-also"></a>另请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

