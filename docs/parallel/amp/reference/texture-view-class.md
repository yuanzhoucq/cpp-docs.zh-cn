---
title: "texture_view 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# texture_view 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供纹理的读取和访问权限。  `texture_view` 只能用于读取值类型是 `int`、`unsigned int` 或 `float` 的具有默认 32 位 bpse 的纹理。  若要了解其他纹理格式，请使用 `texture_view<const _Value_type, _Rank>`。  
  
## 语法  
  
```  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture_view;  
  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture_view : public details::_Texture_base<_Value_type, _Rank>;  
  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture_view<const _Value_type, _Rank> : public details::_Texture_base<_Value_type, _Rank>;  
```  
  
#### 参数  
 `_Value_type`  
 纹理聚合中元素的类型。  
  
 `_Rank`  
 `texture_view` 的秩。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|`value_type`|纹理聚合中元素的类型。|  
|`coordinates_type`|用于指定 `float` 中的纹理的坐标类型，即与关联纹理有相同等级的 `texture_view`，该纹理等级有 `short_vector` 数值类型。|  
|`gather_return_type`|用于收集操作的返回类型，即持有四个相同颜色组件的等级为 4 的 `short_vector`，该组件收集于四个采样的纹理值。|  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[texture\_view::texture\_view 构造函数](../Topic/texture_view::texture_view%20Constructor.md)|已重载。  构造 `texture_view` 实例。|  
|[texture\_view::~texture\_view 析构函数](../Topic/texture_view::~texture_view%20Destructor.md)|销毁 `texture_view` 实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[texture\_view::gather\_alpha 方法](../Topic/texture_view::gather_alpha%20Method.md)|已重载。  使用特定采样配置采样特定坐标的纹理，并返回四个采样的纹理的 Alpha \(w\) 组分。|  
|[texture\_view::gather\_blue 方法](../Topic/texture_view::gather_blue%20Method.md)|已重载。  使用特定采样配置采样特定坐标的纹理，并返回四个采样的纹理的蓝色 \(z\) 组分。|  
|[texture\_view::gather\_green 方法](../Topic/texture_view::gather_green%20Method.md)|已重载。  使用特定采样配置采样特定坐标的纹理，并返回四个采样的纹理的绿色 \(y\) 组分。|  
|[texture\_view::gather\_red 方法](../Topic/texture_view::gather_red%20Method.md)|已重载。  使用特定采样配置采样特定坐标的纹理，并返回四个采样的纹理的红色 \(x\) 组分。|  
|[texture\_view::get 方法](../Topic/texture_view::get%20Method.md)|已重载。  通过索引获取元素值。|  
|[texture\_view::sample 方法](../Topic/texture_view::sample%20Method.md)|已重载。  使用指定的采样配置，采样指定坐标和详细级别的纹理。|  
|[texture\_view::set 方法](../Topic/texture_view::set%20Method.md)|按索引设置元素的值。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[texture\_view::operator\(\) 运算符](../Topic/texture_view::operator\(\)%20Operator.md)|已重载。  通过索引获取元素值。|  
|[texture\_view::operatorOperator](../Topic/texture_view::operatorOperator.md)|已重载。  通过索引获取元素值。|  
|[texture\_view::operator\= 运算符](../Topic/texture_view::operator=%20Operator.md)|已重载。  赋值运算符。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[texture\_view::value\_type 数据成员](../Topic/texture_view::value_type%20Data%20Member.md)|`texture_view` 的元素的值类型。|  
  
## 继承层次结构  
 `_Texture_base`  
  
 `texture_view`  
  
## 要求  
 **标头：**amp\_graphics.h  
  
 **命名空间：**concurrency::graphics  
  
## 请参阅  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)