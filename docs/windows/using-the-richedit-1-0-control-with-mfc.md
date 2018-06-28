---
title: 对 RichEdit 1.0 控件使用 MFC |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d2d45de1c6bd986c2bf509ce601f80fcd3721599
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890306"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>对 RichEdit 1.0 控件使用 MFC
若要使用 RichEdit 控件，必须先调用[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)来加载 RichEdit 2.0 控件 (RICHED20。DLL)，或调用[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)来加载的较旧的 RichEdit 1.0 控件 (RICHED32。DLL)。  
  
 你可以使用当前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)类与较旧的 RichEdit 1.0 控件，但**CRichEditCtrl**不仅旨在支持 RichEdit 2.0 控件。 由于 RichEdit 1.0 和 RichEdit 2.0 是非常相似，将使用的大多数方法;但请注意有一些差异的 1.0 和 2.0 的控件，因此某些方法可能工作不正常或根本无法工作。  
  
## <a name="requirements"></a>要求  
 MFC  
  
## <a name="see-also"></a>请参阅  
 [对话框编辑器疑难解答](../windows/troubleshooting-the-dialog-editor.md)   
 [对话框编辑器](../windows/dialog-editor.md)

