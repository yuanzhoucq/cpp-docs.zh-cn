---
title: "int_2 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::int_2::y
- amp_short_vectors/Concurrency::graphics::int_2::set_x
- amp_short_vectors/Concurrency::graphics::int_2::set_y
- amp_short_vectors/Concurrency::graphics::int_2::get_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator++
- amp_short_vectors/Concurrency::graphics::int_2::x
- amp_short_vectors/Concurrency::graphics::int_2::set_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator/=
- amp_short_vectors/Concurrency::graphics::int_2::get_y
- amp_short_vectors/Concurrency::graphics::int_2::gr
- amp_short_vectors/Concurrency::graphics::int_2::operator*=
- amp_short_vectors/Concurrency::graphics::int_2::r
- amp_short_vectors/Concurrency::graphics::int_2::get_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator=
- amp_short_vectors/Concurrency::graphics::int_2::g
- amp_short_vectors/Concurrency::graphics::int_2::rg
- amp_short_vectors/Concurrency::graphics::int_2::xy
- amp_short_vectors/Concurrency::graphics::int_2::operator-=
- amp_short_vectors/Concurrency::graphics::int_2::get_x
- amp_short_vectors/Concurrency::graphics::int_2::yx
- amp_short_vectors/Concurrency::graphics::int_2
- amp_short_vectors/Concurrency::graphics::int_2::operator-
- amp_short_vectors/Concurrency::graphics::int_2::set_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator+=
- amp_short_vectors/Concurrency::graphics::int_2::operator--
dev_langs:
- C++
ms.assetid: 258b02e9-f1ee-46c2-8edd-dc9f69184846
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 1fb9eba97f469aa407dfe3287a216ceb8f707faf
ms.lasthandoff: 02/24/2017

---
# <a name="int2-class"></a>int_2 类
表示两个整数的短矢量。  
  
## <a name="syntax"></a>语法  
  
```  
class int_2;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[int_2 构造函数](#ctor)|已重载。 默认构造函数，将初始化为 0 的所有元素。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|int_2::get_x 方法||  
|int_2::get_xy 方法||  
|int_2::get_y 方法||  
|int_2::get_yx 方法||  
|int_2::ref_g 方法||  
|int_2::ref_r 方法||  
|int_2::ref_x 方法||  
|int_2::ref_y 方法||  
|int_2::set_x 方法||  
|int_2::set_xy 方法||  
|int_2::set_y 方法||  
|int_2::set_yx 方法||  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|int_2::operator 运算符||  
|int_2::operator-运算符||  
|int_2::operator %= 运算符||  
|int_2::operator < = 运算符||  
|int_2::operator * = 运算符||  
|int_2::operator / = 运算符||  
|int_2::operator ^ = 运算符||  
|int_2::operator | = 运算符||  
|int_2::operator ~ 运算符||  
|int_2::operator + + 运算符||  
|int_2::operator + = 运算符||  
|int_2::operator\<= 运算符||  
|int_2::operator = 运算符||  
|int_2::operator-= 运算符||  
|int_2::operator >> = 运算符||  
  
### <a name="public-constants"></a>公共常量  
  
|名称|说明|  
|----------|-----------------|  
|[大小常量](#int_2__size)||  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|int_2::g 数据成员||  
|int_2::gr 数据成员||  
|int_2::r 数据成员||  
|int_2::rg 数据成员||  
|int_2::x 数据成员||  
|int_2::xy 数据成员||  
|int_2::y 数据成员||  
|int_2::yx 数据成员||  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `int_2`  
  
## <a name="requirements"></a>要求  
 **标头︰** amp_short_vectors.h  
  
 **Namespace:** concurrency:: graphics  
  
##  <a name="a-namectora-int2"></a><a name="ctor"></a>int_2 

 默认构造函数，将初始化为 0 的所有元素。  
  
```  
int_2() restrict(amp,
    cpu);

 
int_2(
    int _V0,  
    int _V1) restrict(amp,
    cpu);

 
int_2(
    int _V) restrict(amp,
    cpu);

 
int_2(
    const int_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
    const uint_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
    const float_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
    const norm_2& _Other) restrict(amp,
    cpu);

 
explicit inline int_2(
    const double_2& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>参数  
 `_V0`  
 要初始化元素 0 的值。  
  
 `_V1`  
 要初始化元素 1 的值。  
  
 `_V`  
 用于初始化值。  
  
 `_Other`  
 用于初始化的对象。  
  
##  <a name="a-nameint2sizea-size"></a><a name="int_2__size"></a>大小 

```  
static const int size = 2;  
```  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency:: graphics Namespace](concurrency-graphics-namespace.md)

