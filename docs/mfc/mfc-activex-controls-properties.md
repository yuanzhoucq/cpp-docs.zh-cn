---
title: MFC ActiveX 控件： 属性 |Microsoft 文档
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
ms.openlocfilehash: ac9d9e4f5e7d777bd147ce36e970e7a30fd875b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-properties"></a>MFC ActiveX 控件：属性
ActiveX 控件，将引发事件，其控件容器与进行通信。 容器，因而将使用方法和属性与控件进行通信。 方法和属性的使用和目的，类似分别是，对成员函数和 c + + 类的成员变量。 属性是对任何容器公开的数据成员的 ActiveX 控件。 属性包含 ActiveX 控件，如自动化客户端和 ActiveX 控件容器应用程序提供的接口。  
  
 属性也称为属性。  
  
 ActiveX 控件方法的详细信息，请参阅文章[MFC ActiveX 控件： 方法](../mfc/mfc-activex-controls-methods.md)。  
  
 ActiveX 控件可以实现 stock 和自定义方法和属性。 类`COleControl`提供的常用属性页的实现。 (常用属性的完整列表，请参阅文章[MFC ActiveX 控件： 添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)。)由开发人员定义的自定义属性添加到 ActiveX 控件的专用的功能。 有关详细信息，请参阅[MFC ActiveX 控件： 添加自定义属性](../mfc/mfc-activex-controls-adding-custom-properties.md)。  
  
 自定义和常用属性，像方法一样，支持通过一种机制组成处理属性和方法以及现有的成员函数的调度映射`COleControl`类。 此外，这些属性可以具有开发人员使用将额外信息传递到控制面板的参数。  
  
 以下文章介绍了更多详细信息中的 ActiveX 控件属性：  
  
-   [MFC ActiveX 控件：添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [MFC ActiveX 控件：添加自定义属性](../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [MFC ActiveX 控件：高级属性实现](../mfc/mfc-activex-controls-advanced-property-implementation.md)  
  
-   [MFC ActiveX 控件：访问环境属性](../mfc/mfc-activex-controls-accessing-ambient-properties.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

