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
ms.openlocfilehash: 99540214d1b903c66d350145c08ab657d12ef8f7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616746"
---
# <a name="dialog-data-validation"></a>对话框数据验证

除了通过调用 DDV 函数，还可以指定验证，如[对话框数据交换](dialog-data-exchange.md)中的示例中所示。 `DDV_MaxChars`示例中的调用验证在文本框控件中输入的字符串的长度是否不超过20个字符。 如果验证失败，DDV 函数通常会向用户发出警报，并将焦点放在冲突的控件上，使用户可以重新输入数据。 对于给定控件，必须在该控件的 DDX 函数之后立即调用 DDV 函数。

还可以定义自己的自定义 DDX 和 DDV 例程。 有关 DDX 和 DDV 的此方面及其他方面的详细信息，请参阅[MFC 技术说明 26](tn026-ddx-and-ddv-routines.md)。

[添加成员变量向导](../ide/add-member-variable-wizard.md)将在数据映射中编写所有的 DDX 和 DDV 调用。

## <a name="see-also"></a>另请参阅

[对话框数据交换和验证](dialog-data-exchange-and-validation.md)<br/>
[在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)<br/>
[对话框数据交换](dialog-data-exchange.md)
