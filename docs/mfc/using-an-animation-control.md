---
title: 使用动画控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecde11ddb55992032b2a8b052e2897a384293bc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382549"
---
# <a name="using-an-animation-control"></a>使用动画控件
动画控件的典型用法遵循以下模式：  
  
-   创建滑块控件。 如果滑块控件是在对话框模板中指定的，则在创建对话框时自动进行创建。 (你应具有[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)对应于动画控件的对话框类中的成员。)或者，可以使用[创建](../mfc/reference/canimatectrl-class.md#create)成员函数来创建控件用作子窗口的任何窗口。  
  
-   加载到动画控件的 AVI 剪辑，通过调用[打开](../mfc/reference/canimatectrl-class.md#open)成员函数。 如果动画控件在对话框中，执行此操作的好时机是在对话框类的[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数。  
  
-   通过调用播放剪辑[播放](../mfc/reference/canimatectrl-class.md#play)成员函数。 如果动画控件在对话框中，执行此操作的好时机是在对话框类的**OnInitDialog**函数。 调用**播放**不是必需的如果在动画控件具有`ACS_AUTOPLAY`样式集。  
  
-   如果你想要显示的剪辑的部分或播放它请逐个框架使用`Seek`成员函数。 若要停止播放剪辑，请使用`Stop`成员函数。  
  
-   如果你不打算立即销毁该控件，剪辑从内存中删除通过调用**关闭**成员函数。  
  
-   如果在动画控件是在对话框中，它与`CAnimateCtrl`将自动销毁对象。 否则，您需要确保正确地销毁控件和 `CAnimateCtrl` 对象。 销毁控件将自动关闭 AVI 剪辑。  
  
## <a name="see-also"></a>请参阅  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控件](../mfc/controls-mfc.md)

