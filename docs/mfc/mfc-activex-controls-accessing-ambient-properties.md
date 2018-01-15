---
title: "MFC ActiveX 控件： 访问环境属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b05e6d37a0550cf157dcd43a22689c9db029b51f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC ActiveX 控件：访问环境属性
本文讨论了 ActiveX 控件可以访问其控件容器的环境属性的方式。  
  
 控件可以通过访问容器的环境属性来获取有关其容器的信息。 这些属性公开可视特性，如容器的背景色，当前字体和所使用的容器，操作特征，如容器是否当前是处于用户模式还是设计器模式。 控件可以使用环境属性来定制它的外观和行为以在其中嵌入的特定容器。 但是，控件应永远不会假定其容器将支持任何特定的环境属性。 事实上，某些容器可能根本不支持任何环境的属性。 在没有环境属性的情况下，控件应假定合理的默认值。  
  
 若要访问环境属性，请调用[COleControl::GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty)。 此函数需要环境属性的调度 ID 作为第一个参数 （OLECTL 的文件。H 定义对标准环境属性集的调度 Id）。  
  
 参数`GetAmbientProperty`函数是调度 ID，variant 类型的值，该值指示应为属性类型，以及指向内存的指针标记应返回值的位置。 此指针引用的数据的类型而异的变体的标记。 该函数将返回**TRUE**如果容器支持的属性，否则它将返回**FALSE**。  
  
 下面的代码示例获取名为"用户模式。"的环境属性的值 如果属性不支持的容器，默认值为**TRUE**假定：  
  
 [!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]  
  
 为方便起见，`COleControl`提供访问许多常用的环境属性，并返回适当的默认值，当属性不可用时的帮助器函数。 这些帮助器函数如下所示：  
  
-   [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)  
  
-   [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)  
  
-   [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)  
  
    > [!NOTE]
    >  调用方必须调用**释放 （）**上返回的字体。  
  
-   [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)  
  
-   [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)  
  
-   [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)  
  
-   [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)  
  
-   [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)  
  
-   [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)  
  
-   [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)  
  
-   [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)  
  
 如果环境属性的值发生更改 （通过容器一些操作中）， **OnAmbientPropertyChanged**调用的控件的成员函数。 重写该成员函数以处理此类的通知。 参数**OnAmbientPropertyChanged**是受影响的环境属性的调度 ID。 此调度 ID 的值可能是**DISPID_UNKNOWN**，指示一个或多个环境的属性已更改，但有关哪些属性受影响的信息不可用。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

