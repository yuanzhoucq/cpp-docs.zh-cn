---
title: MFC ActiveX 控件： 从方法返回错误代码 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdcd18a80b430a0a8576effaaa46215dd5eb9600
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36927914"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX 控件：从方法返回错误代码
本文介绍如何通过 ActiveX 控件方法返回错误代码。  
  
 若要指示方法中发生错误，应使用[colecontrol:: Throwerror](../mfc/reference/colecontrol-class.md#throwerror)成员函数，其将作为参数 SCODE （状态代码）。 你可以使用预定义的 SCODE 或定义你自己的一个。  
  
> [!NOTE]
>  `ThrowError` 意味着仅用作通过属性的 Get 或 Set 函数或自动化方法返回错误的一种方式。 这是适当异常处理程序将出现在堆栈上的唯一时间。  
  
 存在帮助器函数的最常见的预定义 SCODEs，如[colecontrol:: Setnotsupported](../mfc/reference/colecontrol-class.md#setnotsupported)， [colecontrol:: Getnotsupported](../mfc/reference/colecontrol-class.md#getnotsupported)，和[COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
 预定义 SCODEs 和定义自定义 SCODEs 的说明的列表，请参阅明[ActiveX 控件中处理错误](../mfc/mfc-activex-controls-advanced-topics.md)在 ActiveX 控件： 高级主题。  
  
 有关报告代码的异常的其他区域的详细信息，请参阅[COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror)和部分[处理 ActiveX 控件中的错误](../mfc/mfc-activex-controls-advanced-topics.md)在 ActiveX 控件： 高级主题。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

