---
title: MFC ActiveX 控件： 属性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27cdbd548366bcf02e2d6282b309402cf25af2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401610"
---
# <a name="mfc-activex-controls-properties"></a>MFC ActiveX 控件：属性

ActiveX 控件激发其控件容器与进行通信的事件。 容器，作为回报，使用方法和属性与该控件进行通信。 方法和属性是类似的用法和用途，分别为成员函数和 c + + 类的成员变量。 属性是向任何容器公开的数据成员的 ActiveX 控件。 属性包含 ActiveX 控件，如自动化客户端和 ActiveX 控件容器应用程序的提供的接口。

属性也称为属性。

ActiveX 控件方法的详细信息，请参阅文章[MFC ActiveX 控件： 方法](../mfc/mfc-activex-controls-methods.md)。

ActiveX 控件可以实现常用和自定义方法和属性。 类`COleControl`提供常用属性的实现。 (常用属性的完整列表，请参阅文章[MFC ActiveX 控件： 添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)。)由开发人员，定义的自定义属性添加到 ActiveX 控件的专用的功能。 有关详细信息，请参阅[MFC ActiveX 控件： 添加自定义属性](../mfc/mfc-activex-controls-adding-custom-properties.md)。

自定义和常用属性，与方法一样，支持的一种机制组成的调度映射的属性和方法以及现有的成员函数处理`COleControl`类。 此外，这些属性可以有开发人员用于将附加信息传递给该控件的参数。

以下文章讨论了 ActiveX 控件属性的更多详细信息中：

- [MFC ActiveX 控件：添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)

- [MFC ActiveX 控件：添加自定义属性](../mfc/mfc-activex-controls-adding-custom-properties.md)

- [MFC ActiveX 控件：高级属性实现](../mfc/mfc-activex-controls-advanced-property-implementation.md)

- [MFC ActiveX 控件：访问环境属性](../mfc/mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

