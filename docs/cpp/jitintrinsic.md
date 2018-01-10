---
title: "jitintrinsic |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 451f9e534284a2daa69ddc11495f6ecc8af1ee13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="jitintrinsic"></a>jitintrinsic
将函数标记为对 64 位公共语言运行时很有用。 这用于 Microsoft 提供的库中的某些函数。  
  
## <a name="syntax"></a>语法  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>备注  
 `jitintrinsic` 将 MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) 添加到函数签名。  
  
 禁止用户使用该 `__declspec` 修饰符，因为可能出现意外结果。  
  
## <a name="see-also"></a>请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)