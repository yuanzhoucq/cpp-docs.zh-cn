---
title: 链接器工具错误 LNK2039 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 954ea12eb9b49c2bdf59b31a1ec2ec2e66c124ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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