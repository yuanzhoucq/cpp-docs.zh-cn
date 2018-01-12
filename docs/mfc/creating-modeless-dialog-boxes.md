---
title: "创建无模式对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0549f898a076b140e7b5bed23c1c1e8c60d6adba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-modeless-dialog-boxes"></a>创建无模式对话框
对于无模式对话框，您必须在您的对话框类中提供自己的公共构造函数。 若要创建无模式对话框中，调用公共构造函数，，然后调用对话框对象的[创建](../mfc/reference/cdialog-class.md#create)成员函数以加载对话框资源。 你可以调用**创建**期间或之后的构造函数调用。 如果对话框资源具有属性**WS_VISIBLE**，对话框将立即显示。 如果不是，必须调用其[ShowWindow](../mfc/reference/cwnd-class.md#showwindow)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

