---
title: "CDataExchange Class | Microsoft Docs"
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
  - "CDataExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataExchange class"
  - "DDV (dialog data validation)"
  - "DDV (dialog data validation), custom DDV routines"
  - "对话框数据交换 (DDX)"
  - "对话框数据交换 (DDX), between dialog and CDialog"
  - "对话框数据交换 (DDX), custom DDX routines"
  - "对话框数据交换 (DDX), direction of exchange"
  - "DDX/DDV"
  - "DDX/DDV, CDataExchange class"
  - "DDX/DDV, Technical Note 26"
  - "exchanging data between dialogs and CDialogs"
  - "m_bSaveAndValidate"
  - "验证数据, dialog box data entry"
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持数据交换\(ddx\)，而对话数据验证Microsoft基础使用的\(DDV\)实例类别。  
  
## 语法  
  
```  
class CDataExchange  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDataExchange::CDataExchange](../Topic/CDataExchange::CDataExchange.md)|构造 `CDataExchange` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDataExchange::Fail](../Topic/CDataExchange::Fail.md)|调用验证时，会失败。  重置集中到上个月控件和引发异常。|  
|[CDataExchange::PrepareCtrl](../Topic/CDataExchange::PrepareCtrl.md)|所指定的控件为数据交换或验证准备。  nonedit控件的使用。|  
|[CDataExchange::PrepareEditCtrl](../Topic/CDataExchange::PrepareEditCtrl.md)|准备指定的数据交换或验证的编辑控件。|  
|[CDataExchange::PrepareOleCtrl](../Topic/CDataExchange::PrepareOleCtrl.md)|指定的OLE控件为数据交换或验证准备。  nonedit控件的使用。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDataExchange::m\_bSaveAndValidate](../Topic/CDataExchange::m_bSaveAndValidate.md)|DDX和DDV方向的标志。|  
|[CDataExchange::m\_pDlgWnd](../Topic/CDataExchange::m_pDlgWnd.md)|对话框或窗口数据交换出现的位置。|  
  
## 备注  
 `CDataExchange` 没有基类。  
  
 请使用此选件类，如果您为自定义数据类型或控件编写数据交换的实例，或者，如果您要编写自己的数据验证例程。  有关编写DDX和DDV实例的更多信息，请参见 [技术说明26](../../mfc/tn026-ddx-and-ddv-routines.md)。  有关DDX和DDV概述，请参见 [数据交换的对话框和验证](../../mfc/dialog-data-exchange-and-validation.md) 和 [对话框](../../mfc/dialog-boxes.md)。  
  
 `CDataExchange` 对象为DDX和DDV提供所需的上下文信息发生。  当DDX用于从数据成员时，加载对话框控件的初始值标志 `m_bSaveAndValidate` 是 **FALSE**。  标志 `m_bSaveAndValidate` 是 **TRUE**，当DDX用于设置对话框控件的当前值发送到成员时，所以，当DDV用于验证数据值。  如果DDV验证失败，DDV程序将显示将输入解释错误的消息框。  DDV程序将调用 **Fail** 重新将焦点设置到该有问题的控件，并引发异常终止验证过程。  
  
## 继承层次结构  
 `CDataExchange`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例VIEWEX](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)   
 [CWnd::UpdateData](../Topic/CWnd::UpdateData.md)