---
title: 使用包含的窗口
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 5da765eae28d411c98e79af5b9173f48ea66ef8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329307"
---
# <a name="using-contained-windows"></a>使用包含的窗口

ATL 实现包含包含具有[C 包含窗口的窗口](../atl/reference/ccontainedwindowt-class.md)。 包含的窗口表示一个窗口，该窗口将其消息委托给容器对象，而不是在自己的类中处理它们。

> [!NOTE]
> 不需要派生`CContainedWindowT`类，以便使用包含的窗口。

使用包含的窗口，可以超类现有 Windows 类或子类现有窗口。 要创建一个将现有 Windows 类类类超级类的窗口，请先在`CContainedWindowT`对象的构造函数中指定现有类名称。 然后调用`CContainedWindowT::Create`。 要对现有窗口进行子类设置，不需要指定 Windows 类名称（将 NULL 传递给构造函数）。 只需调用`CContainedWindowT::SubclassWindow`方法，对正在下类的窗口的句柄进行调用。

通常使用包含的窗口作为容器类的数据成员。 容器不需要是窗口;因此，容器不需要是窗口。但是，它必须派生自[CMessageMap](../atl/reference/cmessagemap-class.md)。

包含的窗口可以使用备用消息映射来处理其消息。 如果有多个包含的窗口，则应声明多个备用消息映射，每个映射对应于一个单独的包含窗口。

## <a name="example"></a>示例

下面是包含两个包含窗口的容器类的示例：

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

有关包含的窗口的详细信息，请参阅[SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)示例。

## <a name="see-also"></a>另请参阅

[窗口类](../atl/atl-window-classes.md)
