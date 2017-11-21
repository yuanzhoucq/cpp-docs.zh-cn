---
title: "norm 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
dev_langs: C++
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7d35bc7781b1a57fdc0b8b68c5d4f78046d19134
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="norm-class"></a>norm 类
表示范数。 每个元素都浮点数中的范围 [-1.0 f、 1.0 f]。  
  
## <a name="syntax"></a>语法  
  
```  
class norm;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[norm 构造函数](#ctor)|已重载。 默认构造函数。 初始化为 0.0f。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|norm::operator-||  
|norm::operator-||  
|norm::operator float|转换运算符。 将标准数字转换为浮点值。|  
|norm::operator * =||  
|/ = norm::operator 的||  
|norm::operator + +||  
|norm::operator + =||  
|norm::operator =||  
|norm::operator =||  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `norm`  
  
## <a name="requirements"></a>要求  
 **标头：** amp_short_vectors.h  
  
 **Namespace:** concurrency:: graphics  
  
##  <a name="ctor"></a>norm 

 默认构造函数。 初始化为 0.0f。  
  
```  
norm(
    void) restrict(amp,
    cpu);

 
explicit norm(
    float _V) restrict(amp,
    cpu);

 
explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit norm(
    int _V) restrict(amp,
    cpu);

 
explicit norm(
    double _V) restrict(amp,
    cpu);

 
norm(
    const norm& _Other) restrict(amp,
    cpu);

 
norm(
    const unorm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>参数  
 `_V`  
 用来初始化的值。  
  
 `_Other`  
 用于初始化的对象。  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
