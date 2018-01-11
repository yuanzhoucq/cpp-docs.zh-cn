---
title: "C + + 窗口对象与 HWND 之间的关系 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HWND
dev_langs: C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b441077de3a81de569627b6d7acf7cee8ca17b33
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>C++ 窗口对象与 HWND 之间的关系
窗口*对象*是 c + + 对象`CWnd`类 （或派生的类），您的程序直接创建。 它附带并会进入在程序的构造函数和析构函数调用的响应。 Windows*窗口*，另一方面，是 Windows 的内部数据结构，它对应于一个窗口并会占用系统资源时存在一个不透明句柄。 Windows 窗口由"窗口句柄"(`HWND`) 和后创建`CWnd`通过调用创建对象**创建**类的成员函数`CWnd`。 程序调用或用户的操作，可能会销毁窗口。 窗口对象中存储的窗口句柄`m_hWnd`成员变量。 下图显示了 c + + 窗口对象与 Windows 窗口之间的关系。 创建窗口已在[创建 Windows](../mfc/creating-windows.md)。 销毁窗口已在[销毁窗口对象](../mfc/destroying-window-objects.md)。  
  
 ![CWnd 窗口对象和生成的窗口](../mfc/media/vc37fj1.gif "vc37fj1")  
窗口对象和 Windows 窗口  
  
## <a name="see-also"></a>请参阅  
 [窗口对象](../mfc/window-objects.md)

