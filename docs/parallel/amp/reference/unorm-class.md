---
title: "unorm 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
dev_langs:
- C++
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 6817568b7dc111776033e935fd2ba3ad5dc4a69a
ms.lasthandoff: 03/17/2017

---
# <a name="unorm-class"></a>unorm 类
表示 unorm 数。 每个元素是一个浮点数，范围内的 [0.0 f，1.0 f]。  
  
## <a name="syntax"></a>语法  
  
```  
class unorm;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[unorm 构造函数](#ctor)|已重载。 默认构造函数。 初始化为 0.0f。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|unorm::operator-||  
|unorm::operator float|转换运算符。 将 unorm 数字转换为浮点值。|  
|unorm::operator * =||  
|unorm::operator / =||  
|unorm::operator + +||  
|unorm::operator + =||  
|unorm::operator =||  
|unorm::operator =||  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `unorm`  
  
## <a name="requirements"></a>要求  
 **标头︰** amp_short_vectors.h  
  
 **Namespace:** concurrency:: graphics  
  
##  <a name="ctor"></a>unorm 

 默认构造函数。 初始化为 0.0f。  
  
```  
unorm(
    void) restrict(amp,
    cpu);

 
explicit unorm(
    float _V) restrict(amp,
    cpu);

 
explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit unorm(
    int _V) restrict(amp,
    cpu);

 
explicit unorm(
    double _V) restrict(amp,
    cpu);

 
unorm(
    const unorm& _Other) restrict(amp,
    cpu);

 
inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>参数  
 `_V`  
 用来初始化的值。  
  
 `_Other`  
 用于初始化的标准对象。  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)

