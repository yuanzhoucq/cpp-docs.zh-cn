---
title: TN003：将 Windows 句柄映射到对象
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: 46421016171f61a199e6a0a04f6b9b81e260496e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677144"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003：将 Windows 句柄映射到对象

此注释描述 MFC 例程，支持映射 Windows 对象 c + + 对象的句柄。

## <a name="the-problem"></a>问题

Windows 对象通常由各种[处理](/windows/desktop/WinProg/windows-data-types)对象的 MFC 类包装 Windows 对象句柄与 c + + 对象。 句柄的包装函数的 MFC 类库让你找到所包装具有特定的句柄的 Windows 对象的 c + + 对象。 但是，有时对象不具有 c + + 包装器对象，并在这些时间系统创建临时对象来充当 c + + 包装器。

使用句柄映射的 Windows 对象如下所示：

- HWND ([CWnd](../mfc/reference/cwnd-class.md)和`CWnd`的派生类)

- HDC ([CDC](../mfc/reference/cdc-class.md)和`CDC`的派生类)

- HMENU ([CMenu](../mfc/reference/cmenu-class.md))

- HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))

- 套接字 ([CSocket](../mfc/reference/csocket-class.md))

向这些对象的任何一个给定句柄，可以找到通过调用静态方法包装句柄的 MFC 对象`FromHandle`。 例如，假设名为 HWND *hWnd*，下面一行将返回一个指向`CWnd`包装*hWnd*:

```
CWnd::FromHandle(hWnd)
```

如果*hWnd*没有特定的包装器对象，临时`CWnd`创建用于包装*hWnd*。 这样，可以从任何句柄获取有效的 c + + 对象。

包装器对象后，你可以从包装器类的公共成员变量来检索其句柄。 情况下`CWnd`， *m_hWnd*包含该对象的 HWND。

## <a name="attaching-handles-to-mfc-objects"></a>将句柄附加到 MFC 对象

提供给 Windows 对象的新创建的句柄包装器对象和句柄，可以将通过调用两个`Attach`函数如本例所示：

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

这将使条目中永久映射相关联*myWnd*并*hWnd*。 调用`CWnd::FromHandle(hWnd)`现在将返回一个指向*myWnd*。 当*myWnd*是删除，析构函数将自动销毁*hWnd*通过调用 Windows [DestroyWindow](/windows/desktop/api/winuser/nf-winuser-destroywindow)函数。 如果不需要， *hWnd*必须从分离*myWnd*之前*myWnd*被销毁后 (通常，当离开范围*myWnd*已定义)。 `Detach`方法就是如此。

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>有关临时对象的详细信息

创建临时对象的每当`FromHandle`给定还没有包装器对象的句柄。 从其句柄分离再通过删除这些临时对象`DeleteTempMap`函数。 默认情况下[CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle)会自动调用`DeleteTempMap`支持临时句柄映射每个类。 这意味着，不能假定指向临时对象的指针是有效超过从函数退出点在其指针上获取。

## <a name="wrapper-objects-and-multiple-threads"></a>包装器对象和多个线程

临时和永久对象上每个线程进行维护。 也就是说，一个线程无法访问另一个线程的 c + + 包装器对象，而不考虑它是临时还是永久。

若要将这些对象从一个线程传递到另一个，始终将其发送作为其固有`HANDLE`类型。 将 c + + 包装器对象从一个线程传递到另一个通常会导致意外的结果。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)

