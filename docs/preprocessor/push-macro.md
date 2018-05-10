---
title: push_macro |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.push_macro
- push_macro_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, push_macro
- push_macro pragma
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81e41ef7bf7b93e4b2a533dddcb82fee904cb428
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="pushmacro"></a>push_macro
将的值保存*macro_name*堆栈顶端为此宏的宏。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma push_macro("  
macro_name  
")  
  
```  
  
## <a name="remarks"></a>备注  
 你可以检索的值*macro_name*与**pop_macro**。  
  
 请参阅[pop_macro](../preprocessor/pop-macro.md)有关的示例。  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)