---
title: "__based 语法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
ms.openlocfilehash: 427906751c57b8b5f0c46479e8481394fa20f56c
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="based-grammar"></a>__based 语法
## <a name="microsoft-specific"></a>Microsoft 专用  
 在需要精确控制将对象分配到的段（基于静态和动态的数据）时，基寻址很有用。  
  
 32 位和 64 位编译中可接受的基寻址的唯一形式是“基于指针”，它定义一个包含针对 32 位或 64 位基的 32 位或 64 位置换或基于 `void`。  
  
## <a name="grammar"></a>语法  
 *基于范围修饰符*:  
 **__based (***基表达式***)    **  
  
 *基本表达式*:  
 *based-variablebased-abstract-declaratorsegment-namesegment-cast*  
  
 *基于变量*:  
 *identifier*  
  
 *基于抽象声明符*:  
 *抽象声明符*  
  
 *基类型*:  
 *类型名称*  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [基的指针](../cpp/based-pointers-cpp.md)
