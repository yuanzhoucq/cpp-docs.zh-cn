---
title: "auto_inline |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
dev_langs:
- C++
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 455d0b78b5807f92d0b675cd695b998c19abba48
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="autoinline"></a>auto_inline
排除范围内定义的所有函数其中**关闭**指定从考虑为自动内联扩展的候选项。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma auto_inline( [{on | off}] )  
```  
  
## <a name="remarks"></a>备注  
 若要使用**auto_inline**杂注之前, 和之后立即将其放 （不在） 函数定义。 杂注在出现的位置后的第一个函数定义处生效。  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)