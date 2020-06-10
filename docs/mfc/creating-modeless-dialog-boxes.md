---
title: 创建无模式对话框
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 7a6125e84438b0ef2ad541c26bda33051d483c8d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619643"
---
# <a name="creating-modeless-dialog-boxes"></a>创建无模式对话框

对于无模式对话框，您必须在您的对话框类中提供自己的公共构造函数。 若要创建无模式对话框，请调用公共构造函数，然后调用对话框对象的[create](reference/cdialog-class.md#create)成员函数以加载对话框资源。 可以在构造函数调用期间或之后调用**Create** 。 如果对话框资源的属性**WS_VISIBLE**，则对话框将立即显示。 如果不是，则必须调用其[ShowWindow](reference/cwnd-class.md#showwindow)成员函数。

## <a name="see-also"></a>另请参阅

[在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)
