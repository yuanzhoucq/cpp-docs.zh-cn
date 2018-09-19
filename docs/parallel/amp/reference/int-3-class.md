---
title: int_3 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_short_vectors/Concurrency::graphics::int_3::get_x
- amp_short_vectors/Concurrency::graphics::int_3::operator-=
- amp_short_vectors/Concurrency::graphics::int_3::get_y
- amp_short_vectors/Concurrency::graphics::int_3::operator=
- amp_short_vectors/Concurrency::graphics::int_3::operator++
- amp_short_vectors/Concurrency::graphics::int_3::zyx
- amp_short_vectors/Concurrency::graphics::int_3::get_z
- amp_short_vectors/Concurrency::graphics::int_3::operator*=
- amp_short_vectors/Concurrency::graphics::int_3::grb
- amp_short_vectors/Concurrency::graphics::int_3::get_xz
- amp_short_vectors/Concurrency::graphics::int_3::br
- amp_short_vectors/Concurrency::graphics::int_3::operator--
- amp_short_vectors/Concurrency::graphics::int_3
- amp_short_vectors/Concurrency::graphics::int_3::set_yx
- amp_short_vectors/Concurrency::graphics::int_3::x
- amp_short_vectors/Concurrency::graphics::int_3::yxz
- amp_short_vectors/Concurrency::graphics::int_3::set_y
- amp_short_vectors/Concurrency::graphics::int_3::zy
- amp_short_vectors/Concurrency::graphics::int_3::z
- amp_short_vectors/Concurrency::graphics::int_3::get_zx
- amp_short_vectors/Concurrency::graphics::int_3::rb
- amp_short_vectors/Concurrency::graphics::int_3::yzx
- amp_short_vectors/Concurrency::graphics::int_3::gb
- amp_short_vectors/Concurrency::graphics::int_3::set_zxy
- amp_short_vectors/Concurrency::graphics::int_3::xy
- amp_short_vectors/Concurrency::graphics::int_3::set_zx
- amp_short_vectors/Concurrency::graphics::int_3::g
- amp_short_vectors/Concurrency::graphics::int_3::operator/=
- amp_short_vectors/Concurrency::graphics::int_3::get_zy
- amp_short_vectors/Concurrency::graphics::int_3::yx
- amp_short_vectors/Concurrency::graphics::int_3::xzy
- amp_short_vectors/Concurrency::graphics::int_3::set_x
- amp_short_vectors/Concurrency::graphics::int_3::set_xz
- amp_short_vectors/Concurrency::graphics::int_3::get_yzx
- amp_short_vectors/Concurrency::graphics::int_3::b
- amp_short_vectors/Concurrency::graphics::int_3::gbr
- amp_short_vectors/Concurrency::graphics::int_3::operator+=
- amp_short_vectors/Concurrency::graphics::int_3::gr
- amp_short_vectors/Concurrency::graphics::int_3::brg
- amp_short_vectors/Concurrency::graphics::int_3::bg
- amp_short_vectors/Concurrency::graphics::int_3::zx
- amp_short_vectors/Concurrency::graphics::int_3::get_xyz
- amp_short_vectors/Concurrency::graphics::int_3::set_zyx
- amp_short_vectors/Concurrency::graphics::int_3::set_yzx
- amp_short_vectors/Concurrency::graphics::int_3::y
- amp_short_vectors/Concurrency::graphics::int_3::set_z
- amp_short_vectors/Concurrency::graphics::int_3::r
- amp_short_vectors/Concurrency::graphics::int_3::set_xzy
- amp_short_vectors/Concurrency::graphics::int_3::rg
- amp_short_vectors/Concurrency::graphics::int_3::xyz
- amp_short_vectors/Concurrency::graphics::int_3::get_yz
- amp_short_vectors/Concurrency::graphics::int_3::operator-
- amp_short_vectors/Concurrency::graphics::int_3::set_xy
- amp_short_vectors/Concurrency::graphics::int_3::zxy
- amp_short_vectors/Concurrency::graphics::int_3::yz
- amp_short_vectors/Concurrency::graphics::int_3::set_zy
- amp_short_vectors/Concurrency::graphics::int_3::bgr
- amp_short_vectors/Concurrency::graphics::int_3::get_xzy
- amp_short_vectors/Concurrency::graphics::int_3::get_yx
- amp_short_vectors/Concurrency::graphics::int_3::rbg
- amp_short_vectors/Concurrency::graphics::int_3::get_zxy
- amp_short_vectors/Concurrency::graphics::int_3::set_yxz
- amp_short_vectors/Concurrency::graphics::int_3::rgb
- amp_short_vectors/Concurrency::graphics::int_3::get_xy
- amp_short_vectors/Concurrency::graphics::int_3::set_xyz
- amp_short_vectors/Concurrency::graphics::int_3::get_yxz
- amp_short_vectors/Concurrency::graphics::int_3::get_zyx
- amp_short_vectors/Concurrency::graphics::int_3::xz
- amp_short_vectors/Concurrency::graphics::int_3::set_yz
dev_langs:
- C++
ms.assetid: d4af182f-30f1-455c-b16d-aa99cd314038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d1f0f26856d6da002f5ba74bbfa8e98f27e4f02
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042580"
---
# <a name="int3-class"></a>int_3 类
表示三个整数的短矢量。  
  
## <a name="syntax"></a>语法  
  
```  
class int_3;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[int_3 构造函数](#ctor)|已重载。 默认构造函数，初始化 0 的所有元素。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|int_3::get_x||  
|int_3::get_xy||  
|int_3::get_xyz||  
|int_3::get_xz||  
|int_3::get_xzy||  
|int_3::get_y||  
|int_3::get_yx||  
|int_3::get_yxz||  
|int_3::get_yz||  
|int_3::get_yzx||  
|int_3::get_z||  
|int_3::get_zx||  
|int_3::get_zxy||  
|int_3::get_zy||  
|int_3::get_zyx||  
|int_3::ref_b||  
|int_3::ref_g||  
|int_3::ref_r||  
|int_3::ref_x||  
|int_3::ref_y||  
|int_3::ref_z||  
|int_3::set_x||  
|int_3::set_xy||  
|int_3::set_xyz||  
|int_3::set_xz||  
|int_3::set_xzy||  
|int_3::set_y||  
|int_3::set_yx||  
|int_3::set_yxz||  
|int_3::set_yz||  
|int_3::set_yzx||  
|int_3::set_z||  
|int_3::set_zx||  
|int_3::set_zxy||  
|int_3::set_zy||  
|int_3::set_zyx||  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|int_3::operator-||  
|int_3::operator--||  
|int_3::operator%=||  
|int_3::operator&=||  
|int_3::operator*=||  
|int_3::operator/=||  
|int_3::operator^=||  
|int_3::operator&#124;=||  
|int_3::operator~||  
|int_3::operator++||  
|int_3::operator+=||  
|int_3::operator<\<=||  
|int_3::operator=||  
|int_3::operator-=||  
|int_3::operator>>=||  
  
### <a name="public-constants"></a>公共常量  
  
|name|描述|  
|----------|-----------------|  
|[大小常量](#size)||  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|int_3::b||  
|int_3::bg||  
|int_3::bgr||  
|int_3::br||  
|int_3::brg||  
|int_3::g||  
|int_3::gb||  
|int_3::gbr||  
|int_3::gr||  
|int_3::grb||  
|int_3::r||  
|int_3::rb||  
|int_3::rbg||  
|int_3::rg||  
|int_3::rgb||  
|int_3::x||  
|int_3::xy||  
|int_3::xyz||  
|int_3::xz||  
|int_3::xzy||  
|int_3::y||  
|int_3::yx||  
|int_3::yxz||  
|int_3::yz||  
|int_3::yzx||  
|int_3::z||  
|int_3::zx||  
|int_3::zxy||  
|int_3::zy||  
|int_3::zyx||  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `int_3`  
  
## <a name="requirements"></a>要求  
 **标头：** amp_short_vectors.h  
  
 **Namespace:** concurrency:: graphics  

## <a name="ctor"></a> int_3 

默认构造函数，初始化 0 的所有元素。  
  
## <a name="syntax"></a>语法  
  
```  
int_3() restrict(amp,cpu);  
int_3(  
   int _V0,  
   int _V1,  
   int _V2  
) restrict(amp,cpu);  
int_3(  
   int _V  
) restrict(amp,cpu);  
int_3(  
   const int_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const uint_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const float_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const unorm_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const norm_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const double_3& _Other  
) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
*_V0*<br/>
要初始化元素 0 的值。  
  
*_V1*<br/>
要初始化元素 1 的值。  
  
*_V2*<br/>
要初始化元素 2 的值。  
  
*（_V)*<br/>
用于初始化值。  
  
*_Other*<br/>
用于初始化的对象。  
  
## <a name="size"></a> 大小 

## <a name="syntax"></a>语法  
  
```  
static const int size = 3;  
```  
  
## <a name="see-also"></a>请参阅  
 [Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
