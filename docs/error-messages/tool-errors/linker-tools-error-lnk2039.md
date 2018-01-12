---
title: "链接器工具错误 LNK2039 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2039
dev_langs: C++
helpviewer_keywords: LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 441765d85ce65a80102ed94b3f4394ae48c0e29f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2039"></a>链接器工具错误 LNK2039
导入 ref 类\<类型 > 中 another.obj 定义; 它应为导入或定义，但不是能同时  
  
 Ref 类 <`type`> 指定的.obj 文件中导入但在另一个.obj 文件中还会对其进行定义。 此情况可能导致运行时失败或其他意外行为。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查是否必须在其他 .obj 文件中定义“`type`”并检查是否必须从 .winmd 文件导入它。  
  
2.  移除定义或导入。  
  
## <a name="see-also"></a>请参阅  
 [链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)   
 [链接器工具错误 LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)