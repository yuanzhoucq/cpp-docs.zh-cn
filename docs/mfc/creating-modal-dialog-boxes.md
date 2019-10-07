---
title: 创建模式对话框
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed0fe3b7ef8aeddea01f573bfe8e1c01a6b5b443
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685671"
---
# <a name="creating-modal-dialog-boxes"></a>创建模式对话框

若要创建模式对话框，请调用[CDialog](../mfc/reference/cdialog-class.md)中声明的两个公共构造函数之一。 接下来，调用对话框对象的[DoModal](../mfc/reference/cdialog-class.md#domodal)成员函数，以显示对话框并管理与它的交互，直到用户选择 "确定" 或 "取消"。 正是由 `DoModal` 进行的上述管理工作使得对话框成为模式对话框。 对于模式对话框，`DoModal` 将加载对话框资源。

## <a name="see-also"></a>请参阅

[使用 MFC 中的对话框](../mfc/life-cycle-of-a-dialog-box.md)
