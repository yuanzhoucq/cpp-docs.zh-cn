---
title: 创建模式对话框
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed7cc94982a46e542a5174d4d46b8013cc84ffa4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622983"
---
# <a name="creating-modal-dialog-boxes"></a>创建模式对话框

若要创建模式对话框，请调用[CDialog](reference/cdialog-class.md)中声明的两个公共构造函数之一。 接下来，调用对话框对象的[DoModal](reference/cdialog-class.md#domodal)成员函数，以显示对话框并管理与它的交互，直到用户选择 "确定" 或 "取消"。 正是由 `DoModal` 进行的上述管理工作使得对话框成为模式对话框。 对于模式对话框，`DoModal` 将加载对话框资源。

## <a name="see-also"></a>另请参阅

[在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)
