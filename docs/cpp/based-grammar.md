---
title: __based 语法 |Microsoft Docs
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
ms.openlocfilehash: 69d1713b0cc8e1d5d53d3b30f3dd48a0b54a3782
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401956"
---
# <a name="based-grammar"></a>__based 语法
## <a name="microsoft-specific"></a>Microsoft 专用  
 在需要精确控制将对象分配到的段（基于静态和动态的数据）时，基寻址很有用。  
  
 基寻址的 32 位和 64 位编译中可接受"基于指针"的唯一形式，它定义一个包含与 32 位或 64 位基的 32 位或 64 位的位移或基于**void**。  
  
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