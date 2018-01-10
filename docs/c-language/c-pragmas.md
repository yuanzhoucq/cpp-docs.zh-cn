---
title: "C 杂注 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: pragmas, C/C++
ms.assetid: 3d6d36b4-d565-4632-a4cd-e39aeaded5ad
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01fbd345daa6243a0385d556dd7cb6642a881de7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="c-pragmas"></a>C 杂注
**Microsoft 专用**  
  
 “杂注”指示编译器在编译时执行特定操作。 杂注随编译器的不同而不同。 例如，可以使用 optimize 杂注来设置要在程序中执行的优化。 Microsoft C 杂注为：  
  
|||||  
|-|-|-|-|  
|**alloc_text**|**data_seg**|**inline_recursion**|**setlocale**|  
|**auto_inline**|**函数**|**intrinsic**|**warning**|  
|**check_stack**|**hdrstop**|**message**||  
|**code_seg**|**include_alias**|**optimize**||  
|**comment**|**inline_depth**|**pack**||  
  
 有关 Microsoft C 编译器杂注的说明，请参阅《预处理器参考》*中的* [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [源文件和源程序](../c-language/source-files-and-source-programs.md)