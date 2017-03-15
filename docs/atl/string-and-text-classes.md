---
title: "String and Text Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "string classes [ATL]"
  - "字符串转换, ATL"
ms.assetid: aa0cdc41-c953-4b17-82b6-59b908545571
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# String and Text Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些选件类提供针对字符串和文本字符串转换支持。  
  
-   此选件类字符串翻译宏 `CA2TEX` 和 `CT2AEX`和typedef使用[CA2AEX](../atl/reference/ca2aex-class.md)**CA2A**。  
  
-   此选件类字符串翻译宏 `CA2CTEX` 和 `CT2CAEX`和typedef使用[CA2CAEX](../atl/reference/ca2caex-class.md)**CA2CA**。  
  
-   此选件类字符串翻译宏使用[CA2WEX](../atl/reference/ca2wex-class.md)`CA2TEX`、 `CA2CTEX`、 `CT2WEX`和 `CT2CWEX`和typedef **CA2W**。  
  
-   此选件类字符串翻译宏使用[CW2AEX](../atl/reference/cw2aex-class.md)`CT2AEX`、 `CW2TEX`、 `CW2CTEX`和 `CT2CAEX`和typedef **CW2A**。  
  
-   此选件类字符串翻译宏 `CW2CTEX` 和 `CT2CWEX`和typedef使用[CW2CWEX](../atl/reference/cw2cwex-class.md)**CW2CW**。  
  
-   此选件类字符串翻译宏 `CW2TEX` 和 `CT2WEX`和typedef使用[CW2WEX](../atl/reference/cw2wex-class.md)`CW2W`。  
  
-   [CComBSTR](../atl/reference/ccombstr-class.md) 此选件类是 `BSTR`的s.包装。  
  
-   [\_U\_STRINGorID](../atl/reference/u-stringorid-class.md) 此参数适配器选件类允许资源名称\(`LPCTSTR`属于\)或资源ID \(**UINT**属于\)使用 **MAKEINTRESOURCE** 宏，将传递给函数，而无需调用方ID转换为字符串。  
  
## 请参阅  
 [Class Overview](../atl/atl-class-overview.md)   
 [ATL and MFC String Conversion Macros](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)