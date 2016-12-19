---
title: "CMFCMaskedEdit Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCMaskedEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCMaskedEdit class"
  - "CMFCMaskedEdit constructor"
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCMaskedEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCMaskedEdit` 选件类支持掩码编辑控件，验证用户输入掩码并基于模板显示验证的结果。  
  
## 语法  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|默认构造函数。|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCMaskedEdit::DisableMask](../Topic/CMFCMaskedEdit::DisableMask.md)|验证用户输入的禁用。|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](../Topic/CMFCMaskedEdit::EnableGetMaskedCharsOnly.md)|指定 `GetWindowText` 方法是否只检索掩码字符。|  
|[CMFCMaskedEdit::EnableMask](../Topic/CMFCMaskedEdit::EnableMask.md)|初始化掩码编辑控件。|  
|[CMFCMaskedEdit::EnableSelectByGroup](../Topic/CMFCMaskedEdit::EnableSelectByGroup.md)|指定掩码是编辑控件选择用户输入的特定组，或者所有用户输入。|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](../Topic/CMFCMaskedEdit::EnableSetMaskedCharsOnly.md)|指定文本是否仅验证掩码字符，或者所有掩码。|  
|`CMFCMaskedEdit::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCMaskedEdit::GetWindowText](../Topic/CMFCMaskedEdit::GetWindowText.md)|retrieves验证起始于掩码文本编辑控件。|  
|[CMFCMaskedEdit::SetValidChars](../Topic/CMFCMaskedEdit::SetValidChars.md)|指定用户可以输入有效字符的字符串。|  
|[CMFCMaskedEdit::SetWindowText](../Topic/CMFCMaskedEdit::SetWindowText.md)|显示在掩码一个提示编辑控件。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCMaskedEdit::IsMaskedChar](../Topic/CMFCMaskedEdit::IsMaskedChar.md)|调用由结构验证指定的字符对应的掩码字符。|  
  
## 备注  
 执行以下步骤使用 `CMFCMaskedEdit` 控件在您的应用程序:  
  
 1.  嵌入一 `CMFCMaskedEdit` 对象添加到windows选件类。  
  
 2.  调用 [CMFCMaskedEdit::EnableMask](../Topic/CMFCMaskedEdit::EnableMask.md) 方法指定掩码。  
  
 3.  调用 [CMFCMaskedEdit::SetValidChars](../Topic/CMFCMaskedEdit::SetValidChars.md) 方法指定有效字符列表。  
  
 4.  调用 [CMFCMaskedEdit::SetWindowText](../Topic/CMFCMaskedEdit::SetWindowText.md) 方法对掩码指定默认文本编辑控件。  
  
 5.  调用 [CMFCMaskedEdit::GetWindowText](../Topic/CMFCMaskedEdit::GetWindowText.md) 方法检索已验证的文本。  
  
 如果不调用一个或多个方法初始化掩码、有效字符和默认文本，掩码编辑控件的行为就象标准编辑控件的行为。  
  
## 示例  
 下面的示例演示如何设置mask \(例如电话号码\)使用 `EnableMask` 方法创建掩码屏蔽编辑控件，`SetValidChars` 方法指定用户可以输入有效字符的字符串，并且，显示在掩码一个提示的 `SetWindowText` 方法编辑控件。  此示例是 [新的控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/CPP/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/CPP/cmfcmaskededit-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## 要求  
 **标头:** afxmaskededit.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)