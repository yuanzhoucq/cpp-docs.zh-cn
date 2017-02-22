---
title: "C 杂注 | Microsoft Docs"
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
  - "杂注, C/C++"
ms.assetid: 3d6d36b4-d565-4632-a4cd-e39aeaded5ad
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# C 杂注
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 “杂注”指示编译器在编译时执行特定操作。  杂注随编译器的不同而不同。  例如，您可以使用 **optimize** 杂注来设置要在程序中执行的优化。  Microsoft C 杂注为：  
  
|||||  
|-|-|-|-|  
|**alloc\_text**|**data\_seg**|**inline\_recursion**|**setlocale**|  
|**auto\_inline**|**function**|**intrinsic**|**warning**|  
|**check\_stack**|**hdrstop**|**message**||  
|**code\_seg**|**include\_alias**|**optimize**||  
|**comment**|**inline\_depth**|**pack**||  
  
 有关 Microsoft C 编译器杂注的说明，请参阅《预处理器参考》中的[Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [源文件和源程序](../c-language/source-files-and-source-programs.md)