---
title: "TN003：将 Windows 句柄映射到对象 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mapping"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "句柄映射"
  - "映射, 针对对象的 Windows 句柄"
  - "TN003"
  - "针对对象的 Windows 句柄 [C++]"
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# TN003：将 Windows 句柄映射到对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明映射支持窗口对象句柄到 C\+\+ 对象的 MFC 例程。  
  
## 问题  
 窗口对象由 MFC 类包装窗口对象处理 C\+\+ 对象的各 [HANDLE](http://msdn.microsoft.com/library/windows/desktop/aa383751) 对象通常表示。  将 MFC 类库函数的句柄可以找到包装窗口对象具有特殊句柄的 C\+\+ 对象。  但是，有时对象没有 C\+\+. \+\+ 包装对象，并且这些时系统创建临时对象作为 C\+\+ 包装。  
  
 窗口对象使用以及句柄映射\) 如下所示：  
  
-   HWND \([CWnd](../mfc/reference/cwnd-class.md) 和 `CWnd`派生类\)  
  
-   HDC \([CDC](../mfc/reference/cdc-class.md) 和 `CDC`派生类\)  
  
-   HMENU \([CMenu](../mfc/reference/cmenu-class.md)\)  
  
-   HPEN \([CGdiObject](../mfc/reference/cgdiobject-class.md)\)  
  
-   HBRUSH \(`CGdiObject`\)  
  
-   HFONT \(`CGdiObject`\)  
  
-   HBITMAP \(`CGdiObject`\)  
  
-   HPALETTE \(`CGdiObject`\)  
  
-   HRGN \(`CGdiObject`\)  
  
-   HIMAGELIST \([CImageList](../mfc/reference/cimagelist-class.md)\)  
  
-   套接字 \([CSocket](../mfc/reference/csocket-class.md)\)  
  
 将处理对上述任一对象，可以查找通过调用静态方法包装处理 `FromHandle`的 MFC 对象。  例如调用 `hWnd`将 HWND，以下行将返回换行显示 `hWnd`的指针为 `CWnd` :  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 如果 `hWnd` 没有特定的包装对象，临时 `CWnd` 创建一个 `hWnd`包装。  这样就可以从获取所有图柄的有效 C\+\+ 对象。  
  
 在具有包装对象后，则可以从包装类的公共成员变量中检索其处理。  对于 `CWnd`，`m_hWnd` 对象包含该的 HWND。  
  
## 附加指向 MFC 对象的句柄  
 将新创建包装对象的句柄和的句柄窗口对象，可以通过调用 `Attach` 函数将两者关联起来如此示例所示：  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);  
```  
  
 这使得关联在 `myWnd` 和 `hWnd`的永久映射的一项。  调用 `CWnd::FromHandle(hWnd)` 将返回指向 `myWnd`。  当 `myWnd` 删除，析构函数通过调用 Windows 函数 [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682) 自动销毁 `hWnd`。  如果不希望发生，必须从 `myWnd` 分离 `hWnd`，则销毁之前 `myWnd` \(通常，在离开 `myWnd` 定义\) 的大小时。  `Detach` 方法进行此操作。  
  
```  
myWnd.Detach();  
```  
  
## 更多关于临时对象  
 创建临时对象，只要为没有一个包装 `FromHandle` 对象的句柄。  这些临时对象从他们的句柄分离并由 `DeleteTempMap` 函数删除。  默认方法 [CWinThread::OnIdle](../Topic/CWinThread::OnIdle.md) 自动调用支持临时句柄映射的每一个类的 `DeleteTempMap`。  这意味着您不能假定为临时对象的指针中有效的自点从指针获取函数的退出。  
  
## 包装对象和多个线程  
 临时和永久性对象维护每个线程。  即一线程无法访问其他线程 C\+\+ 的包装对象，这与该测试是临时的或永久的。  
  
 要传递一个从线程中的这些对象。另一个，请总是发送它们。这些本机 `HANDLE` 类型。  将 C 文件 . 从一个线程的对象包装到另一个通常导致意外的结果。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)