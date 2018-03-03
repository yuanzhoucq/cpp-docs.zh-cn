---
title: "对 RichEdit 1.0 控件使用 MFC |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d6c5393b006602084a50d18c8cfe76d59d2d6ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-richedit-10-control-with-mfc"></a>对 RichEdit 1.0 控件使用 MFC
若要使用 RichEdit 控件，必须先调用[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)来加载 RichEdit 2.0 控件 (RICHED20。DLL)，或调用[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)来加载的较旧的 RichEdit 1.0 控件 (RICHED32。DLL)。  
  
 你可以使用当前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)类与较旧的 RichEdit 1.0 控件，但**CRichEditCtrl**不仅旨在支持 RichEdit 2.0 控件。 由于 RichEdit 1.0 和 RichEdit 2.0 是非常相似，将使用的大多数方法;但请注意有一些差异的 1.0 和 2.0 的控件，因此某些方法可能工作不正常或根本无法工作。  
  
## <a name="requirements"></a>惠?  
 MFC  
  
## <a name="see-also"></a>请参阅  
 [对话框编辑器疑难解答](../windows/troubleshooting-the-dialog-editor.md)   
 [对话框编辑器](../windows/dialog-editor.md)

