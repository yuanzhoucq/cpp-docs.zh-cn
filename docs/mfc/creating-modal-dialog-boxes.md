---
title: 创建模式对话框 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fcc449a376091c07a7fb26b81fe19752bc3bcd6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376639"
---
# <a name="creating-modal-dialog-boxes"></a>创建模式对话框

若要创建模式对话框，请调用中声明的两个公共构造函数之一[CDialog](../mfc/reference/cdialog-class.md)。 接下来，调用对话框对象的[DoModal](../mfc/reference/cdialog-class.md#domodal)成员函数以显示该对话框并管理与之交互，直到用户选择确定或取消。 正是由 `DoModal` 进行的上述管理工作使得对话框成为模式对话框。 对于模式对话框，`DoModal` 将加载对话框资源。

## <a name="see-also"></a>请参阅

[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

