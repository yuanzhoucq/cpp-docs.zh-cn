---
title: auto_inline |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc1b8a3b8539fb4871e4a28f4635c8012b9f80a2
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42545730"
---
# <a name="autoinline"></a>auto_inline
排除范围内定义的所有函数其中**关闭**从正在被视为候选项为自动内联扩展中指定。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma auto_inline( [{on | off}] )  
```  
  
## <a name="remarks"></a>备注  

若要使用**auto_inline**杂注时，将其放置在之前和之后立即 （不在） 函数定义。 杂注在出现的位置后的第一个函数定义处生效。  
  
## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)