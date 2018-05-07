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
ms.openlocfilehash: 43bf6730cf1b914405f99af6572a0a53cd942ac6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX 控件：从方法返回错误代码
本文介绍如何通过 ActiveX 控件方法返回错误代码。  
  
 若要指示方法中发生错误，应使用[colecontrol:: Throwerror](../mfc/reference/colecontrol-class.md#throwerror)成员函数，其将`SCODE`（状态代码） 作为参数。 您可以使用预定义的 `SCODE`，也可以自己定义一个。  
  
> [!NOTE]
>  `ThrowError` 意味着仅用作通过属性的 Get 或 Set 函数或自动化方法返回错误的一种方式。 这是适当异常处理程序将出现在堆栈上的唯一时间。  
  
 最常见的预定义存在帮助器函数`SCODE`s，如[colecontrol:: Setnotsupported](../mfc/reference/colecontrol-class.md#setnotsupported)， [colecontrol:: Getnotsupported](../mfc/reference/colecontrol-class.md#getnotsupported)，和[COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted)。  
  
 有关的列表预定义`SCODE`s 和定义自定义的说明`SCODE`s，参阅[ActiveX 控件中处理错误](../mfc/mfc-activex-controls-advanced-topics.md)在 ActiveX 控件： 高级主题。  
  
 有关报告代码的异常的其他区域的详细信息，请参阅[COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror)和部分[处理 ActiveX 控件中的错误](../mfc/mfc-activex-controls-advanced-topics.md)在 ActiveX 控件： 高级主题。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

