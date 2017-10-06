---
title: "jitintrinsic |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- jitintrinsic
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6712a62aaff0ff903117da87364cae5bc88580fd
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

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
  
## <a name="see-also"></a>另请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)
