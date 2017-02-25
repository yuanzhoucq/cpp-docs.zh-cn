---
title: "texture 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_graphics/Concurrency::graphics::texture"
dev_langs: 
  - "C++"
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# texture 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

纹理是在范围域中的 `accelerator_view` 上的数据聚合。  它是变量集合，每个元素在范围域中。  每个变量都保留与 C\+\+ 基元类型（`unsigned int`、`int`、`float` 或 `double`）、标量类型（`norm` 或 `unorm`）或短向量类型相对应的值。  
  
## 语法  
  
```  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture;  
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
|`scalar_type`|标量类型。|  
|`value_type`|值类型。|  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[texture::texture 构造函数](../Topic/texture::texture%20Constructor.md)|初始化 [texture](../../../parallel/amp/reference/texture-class.md) 类的新实例。|  
|[texture::~texture 析构函数](../Topic/texture::~texture%20Destructor.md)|销毁[纹理](../../../parallel/amp/reference/texture-class.md)对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[texture::copy\_to 方法](../Topic/texture::copy_to%20Method.md)|通过执行深层复制来将[纹理](../../../parallel/amp/reference/texture-class.md)对象复制到目标。|  
|[texture::data 方法](../Topic/texture::data%20Method.md)|返回 CPU 指针到该纹理的原始数据。|  
|[texture::get 方法](../Topic/texture::get%20Method.md)|返回位于指定索引处的元素的值。|  
|[texture::get\_associated\_accelerator\_view 方法](../Topic/texture::get_associated_accelerator_view%20Method.md)|返回待复制的纹理的优选目标的 [accelerator\_view](../../../parallel/amp/reference/accelerator-view-class.md)。|  
|[texture::get\_depth\_pitch 方法](../Topic/texture::get_depth_pitch%20Method.md)|返回介于 CPU 上 3D 暂存纹理中每个深度切片之间的字节数。|  
|[texture::get\_row\_pitch 方法](../Topic/texture::get_row_pitch%20Method.md)|返回介于 CPU 上 2D 或 3D 暂存纹理中每行之间的字节数。|  
|[texture::set 方法](../Topic/texture::set%20Method.md)|设置指定索引处的元素的值。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[texture::operator\(\) 运算符](../Topic/texture::operator\(\)%20Operator.md)|返回参数指定的元素值。|  
|[texture::operatorOperator](../Topic/texture::operatorOperator.md)|返回位于指定索引处的元素。|  
|[texture::operator\= 运算符](../Topic/texture::operator=%20Operator.md)|将指定的[纹理](../../../parallel/amp/reference/texture-class.md)对象复制到此对象中。|  
  
### 公共常量  
  
|名称|描述|  
|--------|--------|  
|[texture::rank 常量](../Topic/texture::rank%20Constant.md)|获取[纹理](../../../parallel/amp/reference/texture-class.md)对象的秩。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[texture::associated\_accelerator\_view 数据成员](../Topic/texture::associated_accelerator_view%20Data%20Member.md)|获取为将该纹理复制到的首选目标的 [accelerator\_view](../../../parallel/amp/reference/accelerator-view-class.md)。|  
|[texture::depth\_pitch 数据成员](../Topic/texture::depth_pitch%20Data%20Member.md)|获取介于 CPU 上 3D 暂存纹理中的每个深度切片之间的字节数。|  
|[texture::row\_pitch 数据成员](../Topic/texture::row_pitch%20Data%20Member.md)|获取介于 CPU 上 2D 或 3D 暂存纹理中每行之间的字节数。|  
  
## 继承层次结构  
 `_Texture_base`  
  
 `texture`  
  
## 要求  
 **标头：**amp\_graphics.h  
  
 **命名空间：**Concurrency::graphics  
  
## 请参阅  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)