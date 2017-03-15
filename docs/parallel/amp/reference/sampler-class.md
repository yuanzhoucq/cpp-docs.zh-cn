---
title: "sampler 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
caps.latest.revision: 7
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
ms.openlocfilehash: 090e05e294646b7571a3d06ca8ed23583a306756
ms.lasthandoff: 02/24/2017

---
# <a name="sampler-class"></a>sampler 类
采样器类聚合要使用的纹理采样采样配置信息。  
  
## <a name="syntax"></a>语法  
  
```  
class sampler;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[采样器构造函数](#ctor)|已重载。 构造的采样器实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get_address_mode 方法](#get_address_mode)|返回`address_mode`，相关联的采样器对象。|  
|[get_border_color 方法](#get_border_color)|返回的采样器对象相关联的边框颜色。|  
|[get_filter_mode 方法](#get_filter_mode)|返回`filter_mode`，相关联的采样器对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[运算符 = 运算符](#operator_eq)|已重载。 赋值运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[address_mode 数据成员](#address_mode)|获取的地址模式`sampler`对象。|  
|[border_color 数据成员](#border_color)|获取边框颜色的`sampler`对象。|  
|[filter_mode 数据成员](#filter_mode)|获取的筛选器模式`sampler`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `sampler`  
  
## <a name="requirements"></a>要求  
 **标头︰** amp_graphics.h  
  
 **Namespace:** concurrency:: graphics  
  
##  <a name="a-namectora-sampler"></a><a name="ctor"></a>采样器 

 构造一个实例[sampler 类](sampler-class.md)。  
  
```  
sampler() restrict(cpu);

 *// [1] default constructor  
 
sampler(// [2] constructor  
    filter_mode _Filter_mode) restrict(cpu);

 
sampler(// [3] constructor  
    address_mode _Address_mode,  
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

 
sampler(// [4] constructor  
    filter_mode _Filter_mode,  
    address_mode _Address_mode,  
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

 
sampler(// [5] copy constructor  
    const sampler& _Other) restrict(amp,
    cpu);

 
sampler(// [6] move constructor  
    sampler&& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Filter_mode`  
 要在抽样中使用的筛选器模式。  
  
 `_Address_mode`  
 要用于所有维度采样的寻址模式。  
  
 `_Border_color`  
 要使用的寻址模式是否 address_border 边框颜色。 默认值为 `float_4(0.0f, 0.0f, 0.0f, 0.0f)`。  
  
 `_Other`  
 [5] 复制构造函数  
 `sampler`要复制到新对象`sampler`实例。  
  
 [6] 移动构造函数  
 `sampler`对象移动到新`sampler`实例。  
  
##  <a name="a-nameaddressmodea-addressmode"></a><a name="address_mode"></a>address_mode 

 获取的地址模式`sampler`对象。  
  
```  
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;  
```  
  
##  <a name="a-namebordercolora-bordercolor"></a><a name="border_color"></a>border_color 

 获取边框颜色的`sampler`对象。  
  
```  
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;  
```  
  
##  <a name="a-namefiltermodea-filtermode"></a><a name="filter_mode"></a>filter_mode 

 获取的筛选器模式`sampler`对象。  
  
```  
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;  
```  
  
##  <a name="a-namegetaddressmodea-getaddressmode"></a><a name="get_address_mode"></a>get_address_mode 

 返回为此配置的筛选器模式`sampler`。  
  
```  
Concurrency::graphics::address_mode get_address_mode() const __GPU;  
```  
  
### <a name="return-value"></a>返回值  
 配置为采样器寻址模式。  
  
##  <a name="a-namegetbordercolora-getbordercolor"></a><a name="get_border_color"></a>get_border_color 

 返回为此配置的边框颜色`sampler`。  
  
```  
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>返回值  
 Float_4，其中包含的边框颜色。  
  
##  <a name="a-namegetfiltermodea-getfiltermode"></a><a name="get_filter_mode"></a>get_filter_mode 

 返回为此配置的筛选器模式`sampler`。  
  
```  
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>返回值  
 配置为采样器的筛选模式。  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>运算符 = 

 将另一个采样器对象的值分配给现有的采样器。  
  
```  
sampler& operator= (// [1] copy assignment operator const sampler& _Other) restrict(amp,
    cpu);

 
sampler& operator= (// [2] move assingment operator sampler&& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 [1] 复制赋值运算符  
 `sampler`要复制到此对象`sampler`。  
  
 [2] 移动赋值运算符  
 `sampler`对象移动到此`sampler`。  
  
### <a name="return-value"></a>返回值  
 对此采样器实例的引用。  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency:: graphics Namespace](concurrency-graphics-namespace.md)

