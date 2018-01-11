---
title: "销毁框架窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PostNcDestroy
dev_langs: C++
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1cbd96f5044626c7c3c07e8fca115c2b1dca8cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="destroying-frame-windows"></a>销毁框架窗口
MFC 框架管理窗口析构，以及与 framework 文档和视图关联的窗口的创建。 如果你创建其他 windows，你将负责销毁它们。  
  
 在框架中，当用户关闭帧窗口时，窗口的默认[OnClose](../mfc/reference/cwnd-class.md#onclose)处理程序调用[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)。 在销毁 Windows 窗口时调用的最后一个成员函数是[OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)，其中进行一些清理，然后调用[默认](../mfc/reference/cwnd-class.md#default)成员函数来执行 Windows 清理，最后调用虚拟成员函数[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)。 [CFrameWnd](../mfc/reference/cframewnd-class.md)实现`PostNcDestroy`删除 c + + 窗口对象。 你决不应使用 c + +**删除**运算符框架窗口。 请改用 `DestroyWindow`。  
  
 当主窗口关闭时，应用程序关闭。 如果存在修改未保存的文档，框架将显示一个消息框，以询问如果应保存文档，并确保必要时，将保存的相应文档。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [创建文档框架窗口](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)

