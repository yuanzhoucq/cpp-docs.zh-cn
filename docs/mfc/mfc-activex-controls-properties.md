---
title: MFC ActiveX 控件：属性
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: c7ed0fddea660409f5089159b71d39a29b01d538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618182"
---
# <a name="mfc-activex-controls-properties"></a>MFC ActiveX 控件：属性

ActiveX 控件激活事件以便与其控件容器通信。 容器返回，使用方法和属性与控件进行通信。 方法和属性分别与 c + + 类的成员函数和成员变量一起使用和目的相同。 属性是向任何容器公开的 ActiveX 控件的数据成员。 属性为包含 ActiveX 控件的应用程序（例如自动化客户端和 ActiveX 控件容器）提供了一个接口。

属性也称为属性。

有关 ActiveX 控件方法的详细信息，请参阅[MFC ActiveX 控件：方法](mfc-activex-controls-methods.md)一文。

ActiveX 控件可以实现常用和自定义方法和属性。 类 `COleControl` 提供常用属性的实现。 （有关常用属性的完整列表，请参阅[MFC ActiveX 控件：添加常用属性](mfc-activex-controls-adding-stock-properties.md)一文。）自定义属性（由开发人员定义）向 ActiveX 控件添加专用功能。 有关详细信息，请参阅[MFC ActiveX 控件：添加自定义属性](mfc-activex-controls-adding-custom-properties.md)。

自定义属性和常用属性（例如方法）都受一个机制支持，该机制由处理属性和方法的调度映射和类的现有成员函数组成 `COleControl` 。 此外，这些属性还可以包含开发人员用来向控件传递额外信息的参数。

以下文章更详细地讨论了 ActiveX 控件属性：

- [MFC ActiveX 控件：添加常用属性](mfc-activex-controls-adding-stock-properties.md)

- [MFC ActiveX 控件：添加自定义属性](mfc-activex-controls-adding-custom-properties.md)

- [MFC ActiveX 控件：高级属性实现](mfc-activex-controls-advanced-property-implementation.md)

- [MFC ActiveX 控件：访问环境属性](mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
