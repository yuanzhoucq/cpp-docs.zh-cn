---
title: 本地 (MASM) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed9926d23f2e1e8636f31a6f586609ae22d38acd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="local-masm"></a>LOCAL (MASM)
中的第一个指令，宏，内部**本地**定义宏的每个实例是唯一的标签。  
  
## <a name="syntax"></a>语法  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## <a name="remarks"></a>备注  
 在第二个指令，在过程定义中 (**PROC**)，**本地**创建存在过程的持续时间内的基于堆栈的变量。 *标签*可能是简单变量或一个数组，包含*计数*元素。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)