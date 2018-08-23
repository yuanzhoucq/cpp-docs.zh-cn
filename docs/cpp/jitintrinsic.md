---
title: jitintrinsic |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0b114089567de06a71f15b69c556e08d1e4e9c6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404075"
---
# <a name="jitintrinsic"></a>jitintrinsic
将函数标记为对 64 位公共语言运行时很有用。 这用于 Microsoft 提供的库中的某些函数。  
  
## <a name="syntax"></a>语法  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>备注  
 **jitintrinsic**添加 MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) 到函数签名。  
  
 禁止用户使用此 **__declspec**修饰符，意外的结果作为可以发生。  
  
## <a name="see-also"></a>请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)