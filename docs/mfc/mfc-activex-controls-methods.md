---
title: MFC ActiveX 控件：方法
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 9f9ec06852ed0376583363df7649331a0be02105
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621239"
---
# <a name="mfc-activex-controls-methods"></a>MFC ActiveX 控件：方法

ActiveX 控件引发事件，以在其自身与其控件容器之间进行通信。 容器还可以通过方法和属性与控件进行通信。 方法也称为函数。

方法和属性提供导出接口，供其他应用程序（如自动化客户端和 ActiveX 控件容器）使用。 有关 ActiveX 控件属性的详细信息，请参阅[MFC ActiveX 控件：属性](mfc-activex-controls-properties.md)一文。

方法与 c + + 类的成员函数的使用和用途类似。 控件可以实现两种类型的方法： "常用" 和 "自定义"。 与 stock 事件类似，stock 方法是[COleControl](reference/colecontrol-class.md)为其提供实现的方法。 有关常用方法的详细信息，请参阅[MFC ActiveX 控件：添加常用方法](mfc-activex-controls-adding-stock-methods.md)一文。 自定义方法（由开发人员定义）允许对控件进行其他自定义。 有关详细信息，请参阅[MFC ActiveX 控件：添加自定义方法](mfc-activex-controls-adding-custom-methods.md)一文。

Microsoft 基础类库（MFC）实现了一种机制，使控件可以支持常用和自定义方法。 第一部分是 class `COleControl` 。 派生自 `CWnd` ， `COleControl` 成员函数支持所有 ActiveX 控件通用的常用方法。 此机制的第二部分是调度映射。 调度映射类似于消息映射;但是，调度映射将虚拟成员函数映射到 IDispatch ID，而不是将函数映射到 Windows 消息 ID。

为了使控件正确支持各种方法，其类必须声明一个调度映射。 这是通过控件类标头（中的以下代码行来实现的。H）文件：

[!code-cpp[NVC_MFC_AxUI#13](codesnippet/cpp/mfc-activex-controls-methods_1.h)]

调度映射的主要目的是建立外部调用方（如容器）使用的方法名称与实现这些方法的控件类的成员函数之间的关系。 声明调度映射后，需要在控件的实现（中定义）。CPP）文件。 以下代码行将定义调度映射：

[!code-cpp[NVC_MFC_AxUI#14](codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

如果使用[MFC ActiveX 控件向导](reference/mfc-activex-control-wizard.md)创建项目，则会自动添加这些行。 如果未使用 MFC ActiveX 控件向导，则必须手动添加这些行。

以下文章详细介绍了方法：

- [MFC ActiveX 控件：添加常用方法](mfc-activex-controls-adding-stock-methods.md)

- [MFC ActiveX 控件：添加自定义方法](mfc-activex-controls-adding-custom-methods.md)

- [MFC ActiveX 控件：从方法返回错误代码](mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
