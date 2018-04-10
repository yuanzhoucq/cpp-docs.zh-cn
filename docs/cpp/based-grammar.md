---
title: __based 语法 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a2cb2929fa595ad13746ea929217f41272a8189
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
 *类型名称*  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [基的指针](../cpp/based-pointers-cpp.md)