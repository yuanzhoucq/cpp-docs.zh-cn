---
title: MFC ActiveX 控件：方法
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 71c4cdd5ea07b3468b7878a221129a0de5eb4974
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268403"
---
# <a name="mfc-activex-controls-methods"></a>MFC ActiveX 控件：方法

ActiveX 控件触发事件本身和其控件的容器之间进行通信。 容器还可以通过方法和属性通信与控件。 方法也称为函数。

方法和属性提供了导出的接口用于其他应用程序，例如自动化客户端和 ActiveX 控件容器。 ActiveX 控件属性的详细信息，请参阅文章[MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)。

方法是类似于 c + + 类的成员函数的用法和用途。 有两种类型的控件可以实现的方法： 常用和自定义。 常用事件，库存方法类似于这些方法是为其[COleControl](../mfc/reference/colecontrol-class.md)提供实现。 常用方法的详细信息，请参阅文章[MFC ActiveX 控件：添加常用方法](../mfc/mfc-activex-controls-adding-stock-methods.md)。 自定义方法，开发人员，定义允许其他自定义控件。 有关详细信息，请参阅文章[MFC ActiveX 控件：添加自定义方法](../mfc/mfc-activex-controls-adding-custom-methods.md)。

Microsoft 基础类库 (MFC) 实现了一个机制，使控件以支持股票和自定义方法。 第一个部分是类`COleControl`。 派生自`CWnd`，`COleControl`成员函数支持所有 ActiveX 控件都通用的常用方法。 此机制的第二部分是调度映射。 调度映射是类似于消息映射;但是，而不是将函数映射到 Windows 消息 ID，调度映射到 IDispatch ID 映射的虚拟成员函数。

为了使控件可正确支持不同的方法，它的类必须声明调度映射。 这通过下面的代码位于控件类标头行实现 (。H） 文件：

[!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]

调度映射的主要目的是类的使用外部呼叫者 （如容器） 和实现方法的成员函数的控件的方法名称之间建立关系。 已声明调度映射后，需要对其控件的实现中定义 (。CPP) 文件。 以下代码行定义调度映射：

[!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

如果您使用了[MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)若要创建项目时，这些行已自动添加。 如果未使用 MFC ActiveX 控件向导，您必须手动添加这些行。

以下文章介绍了详细信息中的方法：

- [MFC ActiveX 控件：添加常用方法](../mfc/mfc-activex-controls-adding-stock-methods.md)

- [MFC ActiveX 控件：添加自定义方法](../mfc/mfc-activex-controls-adding-custom-methods.md)

- [MFC ActiveX 控件：从方法返回错误代码](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)
