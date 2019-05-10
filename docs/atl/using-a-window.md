---
title: 使用窗口 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
ms.openlocfilehash: 3a1843bfedc30e7d3b47c2916af08c8b53aaa965
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342080"
---
# <a name="using-a-window"></a>使用窗口

类[CWindow](../atl/reference/cwindow-class.md) ，可使用一个窗口。 一旦附加到窗口`CWindow`对象，然后可以调用`CWindow`操作窗口的方法。 `CWindow` 此外包含要转换的 HWND 运算符`CWindow`对象与 HWND。 因此可以传递`CWindow`对象到窗口的句柄所需的任何函数。 您可以轻松地混合`CWindow`方法调用和 Win32 函数调用，而无需创建任何临时对象。

因为`CWindow`有只有两个数据成员 （窗口句柄和的默认尺寸），它不会施加于你的代码开销。 此外，许多的`CWindow`方法只是包装相应的 Win32 API 函数。 通过使用`CWindow`，HWND 成员自动传递给 Win32 函数。

除了使用`CWindow`直接，您也可以派生以将数据或代码添加到您的类。 ATL 本身派生三个类从`CWindow`:[CWindowImpl](../atl/implementing-a-window.md)， [CDialogImpl](../atl/implementing-a-dialog-box.md)，和[CContainedWindowT](../atl/using-contained-windows.md)。

## <a name="see-also"></a>请参阅

[窗口类](../atl/atl-window-classes.md)
