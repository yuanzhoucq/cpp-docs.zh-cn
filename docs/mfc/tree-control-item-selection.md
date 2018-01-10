---
title: "树控件项选择 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b38761b27c21dcf0fe3118d5b73e104cbaaa673d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-item-selection"></a>树控件项选择
当选择从一个项更改到另一个树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 发送[TVN_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547)和[TVN_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544)通知消息。 这两个通知包括指定更改是鼠标单击还是击键的结果的值。 通知还包括有关将获取选择的项和将失去选择的项的信息。 您可以使用此信息设置依赖项的选择状态的项特性。 返回**TRUE**以响应**TVN_SELCHANGING**将防止选择更改; 返回**FALSE**允许更改。  
  
 应用程序可以通过调用来更改所选内容[SelectItem](../mfc/reference/ctreectrl-class.md#selectitem)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

