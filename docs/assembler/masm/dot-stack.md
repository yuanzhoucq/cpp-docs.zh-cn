---
title: .堆栈 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dab47677da8db2afca73a078b110300a017e7c8d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="stack"></a>.STACK
如果用于[。模型](../../assembler/masm/dot-model.md)，定义 （使用段名称堆栈） 堆栈段。 可选`size`指定的堆栈 （默认值 1024） 的字节数。 `.STACK`指令会自动关闭堆栈语句。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STACK [[size]]  
```  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)