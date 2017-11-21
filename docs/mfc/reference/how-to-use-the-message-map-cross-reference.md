---
title: "如何： 使用消息映射交叉引用 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.messages
dev_langs: C++
helpviewer_keywords: windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ffa7b39962d78476e971750e92569eb14229606b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-the-message-map-cross-reference"></a>如何：使用消息映射交叉引用
在标记为条目\<f x n >，编写您自己的成员函数为派生[CWnd](../../mfc/reference/cwnd-class.md)类。 将函数命名为您喜欢的任何名称。 其他函数，如 `OnActivate`，是 `CWnd` 类的成员函数。 如果调用这些函数，则会传递消息给 `DefWindowProc` Windows 函数。 要处理 Windows 通知消息，请重写派生类中相应的 `CWnd` 函数。 您的函数应调用基类中的重写函数使基类和 Windows 响应消息。  
  
 在所有情况下，请将函数原型放在 `CWnd` 派生的类标头中，并对消息映射条目进行编码，如下所示。  
  
 使用了以下术语：  
  
|术语|定义|  
|----------|----------------|  
|id|任何用户定义的菜单项 ID (**WM_COMMAND**消息) 或控件 ID （子窗口通知消息）。|  
|“message”和“wNotifyCode”|在 WINDOWS.H 中定义的 Windows 消息 ID。|  
|nMessageVariable|包含中的返回值的变量名称**RegisterWindowMessage** Windows 函数。|  
  
## <a name="see-also"></a>另请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)

