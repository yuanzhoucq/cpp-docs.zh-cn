---
title: "writeonly_texture_view 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_graphics/Concurrency::graphics::writeonly_texture_view"
dev_langs: 
  - "C++"
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# writeonly_texture_view 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供只写入访问权限给纹理。  
  
## 语法  
  
```  
template <  
   typename _Value_type,  
   int _Rank  
>  
class writeonly_texture_view;  
  
template <  
   typename _Value_type,  
   int _Rank  
>  
class writeonly_texture_view<_Value_type, _Rank> : public details::_Texture_base<_Value_type, _Rank>;  
```  
  
#### 参数  
 `_Value_type`  
 纹理中元素的类型。  
  
 `_Rank`  
 纹理的等级。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|`scalar_type`||  
|`value_type`|纹理中元素的类型。|  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[writeonly\_texture\_view::writeonly\_texture\_view 构造函数](../Topic/writeonly_texture_view::writeonly_texture_view%20Constructor.md)|初始化 [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md) 类的新实例。|  
|[writeonly\_texture\_view::~writeonly\_texture\_view 析构函数:](../Topic/writeonly_texture_view::~writeonly_texture_view%20Destructor.md)|销毁 [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md) 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[writeonly\_texture\_view::set 方法](../Topic/writeonly_texture_view::set%20Method.md)|设置指定索引处的元素的值。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[writeonly\_texture\_view::operator\= 运算符](../Topic/writeonly_texture_view::operator=%20Operator.md)|将指定的 [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md) 对象复制到此对象中。|  
  
### 公共常量  
  
|名称|描述|  
|--------|--------|  
|[writeonly\_texture\_view::rank 常量](../Topic/writeonly_texture_view::rank%20Constant.md)|获取 [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md) 对象的秩。|  
  
## 继承层次结构  
 `_Texture_base`  
  
 `writeonly_texture_view`  
  
## 要求  
 **标头：**amp\_graphics.h  
  
 **命名空间：**Concurrency::graphics  
  
## 请参阅  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)