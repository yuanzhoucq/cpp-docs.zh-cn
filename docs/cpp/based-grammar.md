---
title: __based 语法 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20e1c14cd7add01f8583c24541987b2980da794a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409532"
---
# <a name="based-grammar"></a>__based 语法
## <a name="microsoft-specific"></a>Microsoft 专用  
 在需要精确控制将对象分配到的段（基于静态和动态的数据）时，基寻址很有用。  
  
 32 位和 64 位编译中可接受的基寻址的唯一形式是“基于指针”，它定义一个包含针对 32 位或 64 位基的 32 位或 64 位置换或基于 `void`。  
  
## <a name="grammar"></a>语法  
 *基于范围修饰符*:  
 **__based (***基表达式***)**   
  
 *基本表达式*:  
 *based-variablebased-abstract-declaratorsegment-namesegment-cast*  
  
 *基于变量*:  
 *identifier*  
  
 *基于抽象声明符*:  
 *抽象声明符*  
  
 *基类型*:  
 *type-name*  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [基指针](../cpp/based-pointers-cpp.md)