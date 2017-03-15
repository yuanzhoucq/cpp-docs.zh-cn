---
title: "float_3 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::float_3::get_zyx
- amp_short_vectors/Concurrency::graphics::float_3::set_y
- amp_short_vectors/Concurrency::graphics::float_3::b
- amp_short_vectors/Concurrency::graphics::float_3::operator-=
- amp_short_vectors/Concurrency::graphics::float_3::get_y
- amp_short_vectors/Concurrency::graphics::float_3::set_zy
- amp_short_vectors/Concurrency::graphics::float_3::get_yzx
- amp_short_vectors/Concurrency::graphics::float_3::xz
- amp_short_vectors/Concurrency::graphics::float_3::xyz
- amp_short_vectors/Concurrency::graphics::float_3::operator+=
- amp_short_vectors/Concurrency::graphics::float_3::brg
- amp_short_vectors/Concurrency::graphics::float_3::get_x
- amp_short_vectors/Concurrency::graphics::float_3::get_zx
- amp_short_vectors/Concurrency::graphics::float_3::y
- amp_short_vectors/Concurrency::graphics::float_3::rbg
- amp_short_vectors/Concurrency::graphics::float_3::operator-
- amp_short_vectors/Concurrency::graphics::float_3::get_yz
- amp_short_vectors/Concurrency::graphics::float_3::set_xz
- amp_short_vectors/Concurrency::graphics::float_3::operator/=
- amp_short_vectors/Concurrency::graphics::float_3::zxy
- amp_short_vectors/Concurrency::graphics::float_3::yx
- amp_short_vectors/Concurrency::graphics::float_3::g
- amp_short_vectors/Concurrency::graphics::float_3::r
- amp_short_vectors/Concurrency::graphics::float_3::zy
- amp_short_vectors/Concurrency::graphics::float_3::set_zxy
- amp_short_vectors/Concurrency::graphics::float_3::set_zyx
- amp_short_vectors/Concurrency::graphics::float_3::get_yx
- amp_short_vectors/Concurrency::graphics::float_3
- amp_short_vectors/Concurrency::graphics::float_3::get_xz
- amp_short_vectors/Concurrency::graphics::float_3::get_yxz
- amp_short_vectors/Concurrency::graphics::float_3::set_xy
- amp_short_vectors/Concurrency::graphics::float_3::get_xzy
- amp_short_vectors/Concurrency::graphics::float_3::bgr
- amp_short_vectors/Concurrency::graphics::float_3::zx
- amp_short_vectors/Concurrency::graphics::float_3::gr
- amp_short_vectors/Concurrency::graphics::float_3::set_z
- amp_short_vectors/Concurrency::graphics::float_3::get_zy
- amp_short_vectors/Concurrency::graphics::float_3::gb
- amp_short_vectors/Concurrency::graphics::float_3::set_xzy
- amp_short_vectors/Concurrency::graphics::float_3::set_zx
- amp_short_vectors/Concurrency::graphics::float_3::set_yzx
- amp_short_vectors/Concurrency::graphics::float_3::operator=
- amp_short_vectors/Concurrency::graphics::float_3::x
- amp_short_vectors/Concurrency::graphics::float_3::grb
- amp_short_vectors/Concurrency::graphics::float_3::zyx
- amp_short_vectors/Concurrency::graphics::float_3::set_yxz
- amp_short_vectors/Concurrency::graphics::float_3::get_zxy
- amp_short_vectors/Concurrency::graphics::float_3::set_yz
- amp_short_vectors/Concurrency::graphics::float_3::operator--
- amp_short_vectors/Concurrency::graphics::float_3::set_xyz
- amp_short_vectors/Concurrency::graphics::float_3::operator++
- amp_short_vectors/Concurrency::graphics::float_3::z
- amp_short_vectors/Concurrency::graphics::float_3::xy
- amp_short_vectors/Concurrency::graphics::float_3::rgb
- amp_short_vectors/Concurrency::graphics::float_3::rg
- amp_short_vectors/Concurrency::graphics::float_3::yzx
- amp_short_vectors/Concurrency::graphics::float_3::set_yx
- amp_short_vectors/Concurrency::graphics::float_3::xzy
- amp_short_vectors/Concurrency::graphics::float_3::rb
- amp_short_vectors/Concurrency::graphics::float_3::get_z
- amp_short_vectors/Concurrency::graphics::float_3::br
- amp_short_vectors/Concurrency::graphics::float_3::bg
- amp_short_vectors/Concurrency::graphics::float_3::get_xyz
- amp_short_vectors/Concurrency::graphics::float_3::set_x
- amp_short_vectors/Concurrency::graphics::float_3::yxz
- amp_short_vectors/Concurrency::graphics::float_3::yz
- amp_short_vectors/Concurrency::graphics::float_3::gbr
- amp_short_vectors/Concurrency::graphics::float_3::operator*=
- amp_short_vectors/Concurrency::graphics::float_3::get_xy
dev_langs:
- C++
helpviewer_keywords:
- amp_short_vectors/Concurrency::graphics::float_3
ms.assetid: 209df7a5-08d7-48b4-8ba5-77603642cdd8
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
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 9e1225c724d2c89dd2a6c4158446b6a4df195f6c
ms.lasthandoff: 02/24/2017

---
# <a name="float3-class"></a>float_3 类
表示三个浮点型值的短矢量。  
  
## <a name="syntax"></a>语法  
  
```  
class float_3;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[float_3 构造函数](#ctor)|已重载。 默认构造函数，将初始化为 0 的所有元素。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|float_3::get_x 方法||  
|float_3::get_xy 方法||  
|float_3::get_xyz 方法||  
|float_3::get_xz 方法||  
|float_3::get_xzy 方法||  
|float_3::get_y 方法||  
|float_3::get_yx 方法||  
|float_3::get_yxz 方法||  
|float_3::get_yz 方法||  
|float_3::get_yzx 方法||  
|float_3::get_z 方法||  
|float_3::get_zx 方法||  
|float_3::get_zxy 方法||  
|float_3::get_zy 方法||  
|float_3::get_zyx 方法||  
|float_3::ref_b 方法||  
|float_3::ref_g 方法||  
|float_3::ref_r 方法||  
|float_3::ref_x 方法||  
|float_3::ref_y 方法||  
|float_3::ref_z 方法||  
|float_3::set_x 方法||  
|float_3::set_xy 方法||  
|float_3::set_xyz 方法||  
|float_3::set_xz 方法||  
|float_3::set_xzy 方法||  
|float_3::set_y 方法||  
|float_3::set_yx 方法||  
|float_3::set_yxz 方法||  
|float_3::set_yz 方法||  
|float_3::set_yzx 方法||  
|float_3::set_z 方法||  
|float_3::set_zx 方法||  
|float_3::set_zxy 方法||  
|float_3::set_zy 方法||  
|float_3::set_zyx 方法||  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|float_3::operator 运算符||  
|float_3::operator-运算符||  
|float_3::operator * = 运算符||  
|float_3::operator / = 运算符||  
|float_3::operator + + 运算符||  
|float_3::operator + = 运算符||  
|float_3::operator = 运算符||  
|float_3::operator-= 运算符||  
  
### <a name="public-constants"></a>公共常量  
  
|名称|说明|  
|----------|-----------------|  
|[大小常量](#float_3__size)||  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|float_3::b 数据成员||  
|float_3::bg 数据成员||  
|float_3::bgr 数据成员||  
|float_3::br 数据成员||  
|float_3::brg 数据成员||  
|float_3::g 数据成员||  
|float_3::gb 数据成员||  
|float_3::gbr 数据成员||  
|float_3::gr 数据成员||  
|float_3::grb 数据成员||  
|float_3::r 数据成员||  
|float_3::rb 数据成员||  
|float_3::rbg 数据成员||  
|float_3::rg 数据成员||  
|float_3::rgb 数据成员||  
|float_3::x 数据成员||  
|float_3::xy 数据成员||  
|float_3::xyz 数据成员||  
|float_3::xz 数据成员||  
|float_3::xzy 数据成员||  
|float_3::y 数据成员||  
|float_3::yx 数据成员||  
|float_3::yxz 数据成员||  
|float_3::yz 数据成员||  
|float_3::yzx 数据成员||  
|float_3::z 数据成员||  
|float_3::zx 数据成员||  
|float_3::zxy 数据成员||  
|float_3::zy 数据成员||  
|float_3::zyx 数据成员||  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `float_3`  
  
## <a name="requirements"></a>要求  
 **标头︰** amp_short_vectors.h  
  
 **Namespace:** concurrency:: graphics  
  
##  <a name="a-namectora-float3"></a><a name="ctor"></a>float_3 

 默认构造函数，将初始化为 0 的所有元素。  
  
```  
float_3() restrict(amp,
    cpu);

 
float_3(
    float _V0,  
    float _V1,  
    float _V2) restrict(amp,
    cpu);

 
float_3(
    float _V) restrict(amp,
    cpu);

 
float_3(
    const float_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const uint_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const int_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const unorm_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const norm_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const double_3& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>参数  
 `_V0`  
 要初始化元素 0 的值。  
  
 `_V1`  
 要初始化元素 1 的值。  
  
 `_V2`  
 要初始化元素 2 的值。  
  
 `_V`  
 用于初始化值。  
  
 `_Other`  
 用于初始化的对象。  
  
##  <a name="a-namefloat3sizea-size"></a><a name="float_3__size"></a>大小 

```  
static const int size = 3;  
```  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency:: graphics Namespace](concurrency-graphics-namespace.md)

