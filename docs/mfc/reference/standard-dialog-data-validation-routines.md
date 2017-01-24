---
title: "标准对话框数据验证例程 | Microsoft Docs"
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
  - "标准对话框, 数据验证例程"
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
caps.latest.revision: 13
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 标准对话框数据验证例程
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此主题列出了用于常见 MFC 对话框控件的标准对话框数据验证 \(DDV\) 例程。  
  
> [!NOTE]
>  标准对话框数据交换例程在头文件 afxdd\_.h 中定义。  但是，您的应用程序应该包括 afxwin.h。  
  
### DDV 函数  
  
|||  
|-|-|  
|[DDV\_MaxChars](../Topic/DDV_MaxChars.md)|验证给定控件值的字符数的数字不超过给定的最大数。|  
|[DDV\_MinMaxByte](../Topic/DDV_MinMaxByte.md)|验证给定控件值不超出给定的 **BYTE** 范围。|  
|[DDV\_MinMaxDateTime](../Topic/DDV_MinMaxDateTime.md)|验证给定控件值不超出给定的时间范围。|  
|[DDV\_MinMaxDouble](../Topic/DDV_MinMaxDouble.md)|验证给定控件值不超出给定的 **double** 范围。|  
|[DDV\_MinMaxDWord](../Topic/DDV_MinMaxDWord.md)|验证给定控件值不超出给定的 **DWORD** 范围。|  
|[DDV\_MinMaxFloat](../Topic/DDV_MinMaxFloat.md)|验证给定控件值不超出给定的 **float** 范围。|  
|[DDV\_MinMaxInt](../Topic/DDV_MinMaxInt.md)|验证给定控件值不超出给定的 **int** 范围。|  
|[DDV\_MinMaxLong](../Topic/DDV_MinMaxLong.md)|验证给定控件值不超出给定的 **long** 范围。|  
|[DDV\_MinMaxLongLong](../Topic/DDV_MinMaxLongLong.md)|验证给定控件值不超出给定的 **LONGLONG** 范围。|  
|[DDV\_MinMaxMonth](../Topic/DDV_MinMaxMonth.md)|验证给定控件值不超出给定的日期范围。|  
|[DDV\_MinMaxShort](../Topic/DDV_MinMaxShort.md)|验证给定控件值不超出给定的 **short** 范围。|  
|[DDV\_MinMaxSlider](../Topic/DDV_MinMaxSlider.md)|验证给定滑动条控件的值落到给定范围中。|  
|[DDV\_MinMaxUInt](../Topic/DDV_MinMaxUInt.md)|验证给定控件值不超出给定的 **UINT** 范围。|  
|[DDV\_MinMaxULongLong](../Topic/DDV_MinMaxULongLong.md)|验证给定控件值不超出给定的 **ULONGLONG** 范围。|  
  
## 请参阅  
 [标准对话框数据交换例程](../../mfc/reference/standard-dialog-data-exchange-routines.md)   
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)