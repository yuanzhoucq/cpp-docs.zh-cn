---
title: TN003： 的 Windows 句柄映射到对象 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mapping
dev_langs:
- C++
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2be47da802fd1168ec7b43c2f7701351b3c88d8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951503"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003：将 Windows 句柄映射到对象
此注释描述 MFC 例程，支持将映射 Windows 对象句柄到 c + + 对象。  
  
## <a name="the-problem"></a>问题  
 Windows 对象通常表示由各种[处理](http://msdn.microsoft.com/library/windows/desktop/aa383751)对象的 MFC 类包装 Windows 对象句柄与 c + + 对象。 句柄的包装的 MFC 类库函数可以查找具有特定的句柄的 Windows 对象包装的 c + + 对象。 但是，有时对象不具有 c + + 包装器对象，并在这些时间系统创建临时对象来充当 c + + 包装器。  
  
 使用句柄映射的 Windows 对象如下所示：  
  
-   HWND ([CWnd](../mfc/reference/cwnd-class.md)和`CWnd`-派生类)  
  
-   HDC ([CDC](../mfc/reference/cdc-class.md)和`CDC`-派生类)  
  
-   HMENU ([CMenu](../mfc/reference/cmenu-class.md))  
  
-   HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))  
  
-   HBRUSH (`CGdiObject`)  
  
-   HFONT (`CGdiObject`)  
  
-   HBITMAP (`CGdiObject`)  
  
-   HPALETTE (`CGdiObject`)  
  
-   HRGN (`CGdiObject`)  
  
-   HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))  
  
-   套接字 ([CSocket](../mfc/reference/csocket-class.md))  
  
 提供这些对象的任何一个的句柄，你可找到通过调用静态方法包装的句柄 MFC 对象`FromHandle`。 例如，给定调用 HWND *hWnd*，下面一行将返回一个指向`CWnd`包装*hWnd*:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 如果*hWnd*没有特定的包装器对象，一个临时`CWnd`创建包装*hWnd*。 这使它可以从任何句柄获取有效的 c + + 对象。  
  
 一个包装对象后，你可以从包装器类的公共成员变量中检索其句柄。 情况下`CWnd`， *m_hWnd*包含该对象的 HWND。  
  
## <a name="attaching-handles-to-mfc-objects"></a>附加到 MFC 对象的句柄  
 新创建的句柄包装对象与句柄提供给 Windows 对象时，你可以将关联这两种调用`Attach`函数如此示例所示：  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);
```  
  
 这样，在永久映射关联条目*myWnd*和*hWnd*。 调用`CWnd::FromHandle(hWnd)`现在将返回一个指向*myWnd*。 当*myWnd*是删除，析构函数将自动销毁*hWnd*通过调用 Windows [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682)函数。 如果这不所需， *hWnd*必须分离*myWnd*之前*myWnd*被销毁 (通常，当保留该作用域内*myWnd*已定义)。 `Detach`方法。  
  
```  
myWnd.Detach();
```  
  
## <a name="more-about-temporary-objects"></a>有关临时对象的详细信息  
 创建临时对象每当`FromHandle`给定尚不包含包装器对象的句柄。 从其句柄分离和删除这些临时对象`DeleteTempMap`函数。 默认情况下[CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle)自动调用`DeleteTempMap`支持临时句柄映射每个类。 这意味着，你不能假设指向临时对象的指针将有效的函数退出点之后在获取指针。  
  
## <a name="wrapper-objects-and-multiple-threads"></a>包装器对象和多个线程  
 临时和永久对象保持的每个线程基础上。 它是一个线程无法访问另一个线程的 c + + 包装器对象，无论它是临时的还是永久。  
  
 若要将这些对象从一个线程传递给另一个，始终将发送它们作为其本机`HANDLE`类型。 将 c + + 包装器对象从一个线程传递到另一个将通常会导致意外的结果。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

