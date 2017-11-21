---
title: "对话框数据验证 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 58fbff4a5192d15a60cf3340ce762574947fb249
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="dialog-data-validation"></a>对话框数据验证
中的示例中所示，可以通过调用 DDV 函数指定除了数据交换的验证[对话框数据交换](../mfc/dialog-data-exchange.md)。 `DDV_MaxChars`在示例中调用验证输入的文本框控件中的字符串不超过 20 个字符。 如果验证失败，并将焦点置于有问题的控件上，以便用户可以重新输入数据，DDV 函数通常向具有一个消息框的用户发出警报。 给定控件的 DDV 函数必须为相同的控件的 DDX 函数之后立即调用。  
  
 你还可以定义自己的自定义 DDX 和 DDV 例程。 此选项及 DDX 和 DDV 的其他方面的详细信息，请参阅[MFC 技术说明 26](../mfc/tn026-ddx-and-ddv-routines.md)。  
  
 [添加成员变量向导](../ide/add-member-variable-wizard.md)将写入所有 DDX 和 DDV 在为你在数据映射中调用。  
  
## <a name="see-also"></a>另请参阅  
 [对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [对话框数据交换](../mfc/dialog-data-exchange.md)

