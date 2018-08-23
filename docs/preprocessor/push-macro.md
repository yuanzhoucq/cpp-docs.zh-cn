---
title: push_macro |Microsoft Docs
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
ms.openlocfilehash: 70b472ba11445cdc5aa2a192d02d82c51d724b8c
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42543078"
---
# <a name="pushmacro"></a>push_macro
将值保存*macro_name*为此宏堆栈顶部的宏。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma push_macro("  
macro_name  
")  
```  
  
## <a name="remarks"></a>备注  
 
可以检索的值*macro_name*与`pop_macro`。  
  
请参阅[pop_macro](../preprocessor/pop-macro.md)有关的示例。  
  
## <a name="see-also"></a>请参阅  
 
[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)