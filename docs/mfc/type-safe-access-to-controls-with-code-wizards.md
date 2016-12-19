---
title: "通过代码向导对控件进行类型安全的访问 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "代码向导"
  - "对话框数据交换 (DDX), 访问控件"
  - "对话框控件, 访问"
  - "对话框, 访问控件"
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 通过代码向导对控件进行类型安全的访问
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果熟悉 DDX 功能，可以在 [添加成员变量向导](../ide/add-member-variable-wizard.md) 中使用控件属性创建类型安全访问。  此方法比创建控件容易没有代码向导。  
  
 如果需要对控件的访问，DDX 提供类型。  如果希望执行多于访问控件的值，请使用"添加成员变量向导添加适当类的对话框成员变量添加到类。  附加此成员变量设置控件属性。  
  
 成员变量可以具有控件属性而不是属性值。  属性值引用这些控件返回的数据类型，例如 `CString` 或 `int`。  通过控件属性类型是某个的 MFC 控件类，如 `CButton` 或 `CEdit`的数据成员来实现对控件的直接访问。  
  
> [!NOTE]
>  对于给定控件，则可以，因此，如果不具有，属性值的多个变量和成员通常与控件属性的成员变量。  因为多次对象附加到控件，或者任何其他窗口，将生成消息映射的多义性，只能具有 MFC 对象映射到控件。  
  
 您可以使用此对象调用控件对象的所有成员函数。  这些调用影响在对话框的控件。  例如，对于，变量 `m_Checkbox`表示的复选框控件，`CButton`类型，您可能调用：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/CPP/type-safe-access-to-controls-with-code-wizards_1.cpp)]  
  
 此处成员变量 `m_Checkbox` 为用途和成员函数在 [对控件类型的安全访问没有代码向导](../mfc/type-safe-access-to-controls-without-code-wizards.md)显示的 `GetMyCheckbox` 相同。  如果复选框是一自动复选框，可以将 **BN\_CLICKED** 控件通知消息的对话框类需要处理程序，在单击按钮时。  
  
 有关该控件的更多信息，请参见 [控件](../mfc/controls-mfc.md)。  
  
## 请参阅  
 [对对话框中的控件进行类型安全的访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [不通过代码向导对控件进行类型安全的访问](../mfc/type-safe-access-to-controls-without-code-wizards.md)