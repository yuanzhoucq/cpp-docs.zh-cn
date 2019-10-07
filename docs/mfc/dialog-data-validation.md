---
title: 对话框数据验证
ms.date: 11/04/2016
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
ms.openlocfilehash: c89ed82b148062ddb64fa85eaabda12f44e59895
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685764"
---
# <a name="dialog-data-validation"></a>对话框数据验证

除了通过调用 DDV 函数，还可以指定验证，如[对话框数据交换](../mfc/dialog-data-exchange.md)中的示例中所示。 示例中的 `DDV_MaxChars` 调用用于验证在文本框控件中输入的字符串的长度是否不超过20个字符。 如果验证失败，DDV 函数通常会向用户发出警报，并将焦点放在冲突的控件上，使用户可以重新输入数据。 对于给定控件，必须在该控件的 DDX 函数之后立即调用 DDV 函数。

还可以定义自己的自定义 DDX 和 DDV 例程。 有关 DDX 和 DDV 的此方面及其他方面的详细信息，请参阅[MFC 技术说明 26](../mfc/tn026-ddx-and-ddv-routines.md)。

[添加成员变量向导](../ide/add-member-variable-wizard.md)将在数据映射中编写所有的 DDX 和 DDV 调用。

## <a name="see-also"></a>请参阅

[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)<br/>
[使用 MFC 中的对话框](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[对话框数据交换](../mfc/dialog-data-exchange.md)
