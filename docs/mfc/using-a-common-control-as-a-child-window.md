---
title: 将公共控件用作子窗口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50d21675d913211026a2077a0830b7d8ed1225c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-common-control-as-a-child-window"></a>将公共控件用作子窗口
任何一个 Windows 公共控件均可用作任何其他窗口的子窗口。 以下过程介绍如何以动态方式创建公共控件然后使用它。  
  
### <a name="to-use-a-common-control-as-a-child-window"></a>将公共控件用作子窗口  
  
1.  在相关类或处理程序中定义控件。  
  
2.  使用的控件的重写[cwnd:: Create](../mfc/reference/cwnd-class.md#create)方法来创建 Windows 控件。  
  
3.  创建控件后（如果创建控件的子类，则是在执行 `OnCreate` 处理程序的时候），可使用其成员函数操作控件。 请参阅在单独的控件的说明[控件](../mfc/controls-mfc.md)有关方法的详细信息。  
  
4.  当使用完控件，请使用[cwnd:: Destroywindow](../mfc/reference/cwnd-class.md#destroywindow)销毁控件。  
  
## <a name="see-also"></a>请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)

