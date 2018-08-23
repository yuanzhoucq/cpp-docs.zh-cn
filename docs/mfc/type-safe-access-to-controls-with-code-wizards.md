---
title: 通过代码向导对控件的类型安全访问 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88f86a8f22bae990261be5150755a26d50d4bef8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950456"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>通过代码向导对控件进行类型安全的访问
如果你熟悉 DDX 功能，你可以使用中的控件属性[添加成员变量向导](../ide/add-member-variable-wizard.md)创建类型安全访问。 这种方法是比创建控件而不通过代码向导更容易。  
  
 如果你只想对控件的值的访问，DDX 将提供它。 如果你想要多个访问控件的值，使用添加成员变量向导将适当的类的成员变量添加到对话框类。 将此成员变量附加到控件属性。  
  
 成员变量可以具有而不是值属性的控件属性。 Value 属性是指通过控件，如返回的数据类型`CString`或**int**。控件属性用于直接访问控制通过其类型是在 MFC 中的控件类之一如的数据成员`CButton`或`CEdit`。  
  
> [!NOTE]
>  对于给定的控件，你，如果您愿意，可以用值的属性和最多的控件属性的一个成员变量的多个成员变量。 你可以映射到控件，因为多个对象附加到控件或任何其他窗口时，会导致多义性的消息映射中只有一个 MFC 对象。  
  
 此对象可用于为控件对象调用任何成员函数。 此类调用会影响在对话框中的控件。 例如，复选框控件表示由变量*m_Checkbox*，类型的`CButton`，您可以调用：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]  
  
 此处的成员变量*m_Checkbox*提供成员函数相同的目的`GetMyCheckbox`中所示[控件没有代码向导对类型安全的访问](../mfc/type-safe-access-to-controls-without-code-wizards.md)。 如果复选框不是自动复选框，则仍需要处理程序对话框类 BN_CLICKED 控件通知消息中单击该按钮。  
  
 有关控件的详细信息，请参阅[控件](../mfc/controls-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [对在对话框中的控件类型安全访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [对控件进行类型安全的访问（不使用代码向导）](../mfc/type-safe-access-to-controls-without-code-wizards.md)

