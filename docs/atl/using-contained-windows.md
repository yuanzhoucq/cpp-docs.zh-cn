---
title: 使用包含的 Windows |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1d338851a6480014e1f7a48f848f95439d9311a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762107"
---
# <a name="using-contained-windows"></a>使用包含的 Windows

ATL 实现与包含的 windows [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)。 包含的窗口表示委托给容器对象，而不是在其自己的类中处理这些消息的窗口。

> [!NOTE]
>  不需要从派生类`CContainedWindowT`若要使用包含的窗口。

使用包含的窗口，您可以创建超类现有的 Windows 类或子类现有窗口。 若要创建窗口创建超类现有的 Windows 类中，第一次的构造函数中指定现有的类名`CContainedWindowT`对象。 然后，调用`CContainedWindowT::Create`。 为现有窗口的子类，不需要指定 Windows 类名称 （向构造函数传递 NULL）。 只需调用`CContainedWindowT::SubclassWindow`与正在子类化窗口的句柄的方法。

您通常用作容器类的数据成员包含的窗口。 容器不需要是窗口;但是，它必须派生自[CMessageMap](../atl/reference/cmessagemap-class.md)。

包含的窗口可以使用备用消息映射来处理其消息。 如果有多个包含的窗口，您应声明多个备用消息映射，每个对应于包含单独的窗口。

## <a name="example"></a>示例

以下是具有两个包含的窗口的容器类的示例：

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

有关包含的窗口的详细信息，请参阅[SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)示例。

## <a name="see-also"></a>请参阅

[窗口类](../atl/atl-window-classes.md)

