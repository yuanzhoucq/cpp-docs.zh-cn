---
title: "extent 类 (c + + AMP) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
dev_langs: C++
helpviewer_keywords: extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 22b7a25d0695b7e12a4fbecbf47bbc7feb32148f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="extent-class-c-amp"></a>extent 类 (C++ AMP)
表示向量*N*指定的边界的整数值*N*-具有 0 来源的维空间。 向量中的值是从最高有效订购到最不重要。  
  
### <a name="syntax"></a>语法  
  
```  
template <int _Rank>  
class extent;  
```  
  
### <a name="parameters"></a>参数  
 `_Rank`  
 秩`extent`对象。  

 ## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[范围构造函数](#ctor)|初始化 `extent` 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[包含](#contains)|验证指定`extent`对象具有指定的秩。|  
|[size](#size)|返回 （中的元素的单位） 的范围的总线性大小。|  
|[磁贴](#tile)|生成`tiled_extent`指定维度与给定的磁贴扩展盘区的对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator-](#operator_min)|返回一个新`extent`通过减去创建的对象`index`从相应的元素`extent`元素。|  
|[operator--](#operator_min_min)|递减的每个元素`extent`对象。|  
|[operator%=](#operator_mod_eq)|计算中每个元素的模数 （余数）`extent`对象时该元素除以一个数字。|  
|[operator*=](#operator_star_eq)|乘以的每个元素`extent`大量对象。|  
|[operator/=](#operator_min_eq)|将划分的每个元素`extent`大量对象。|  
|[extent:: operator\[\]](#operator_at)|返回位于指定索引处的元素。|  
|[operator+](#operator_add)|返回一个新`extent`创建通过添加相应的对象`index`和`extent`元素。|  
|[operator++](#operator_add_add)|递增的每个元素`extent`对象。|  
|[operator+=](#operator_add_eq)|将指定的数添加到的每个元素`extent`对象。|  
|[operator=](#operator_eq)|将另一个的内容复制`extent`到此对象。|  
|[operator-=](#operator_min_eq)|减去指定的数目的每个元素`extent`对象。|  

  
### <a name="public-constants"></a>公共常量  
  
|名称|描述|  
|----------|-----------------|  
|[rank 常量](#rank)|获取的秩`extent`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `extent`  


## <a name="contains"></a>包含 

指示是否指定[索引](index-class.md)值包含在该范围对象。  
  
### <a name="syntax"></a>语法  
  
```  
bool contains(const index<rank>& _Index) const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 `index`要测试值。  
  
### <a name="return-value"></a>返回值  
 `true`如果指定`index`值包含在`extent`对象; 否则为`false`。  
  
##  <a name="ctor"></a>范围 

初始化范围类的新实例。  
  
### <a name="syntax"></a>语法  
  
```  
extent() restrict(amp,cpu);    
extent(const extent<_Rank>& _Other) restrict(amp,cpu);    
explicit extent(int _I) restrict(amp,cpu);    
extent(int _I0,  int _I1) restrict(amp,cpu);    
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);    
explicit extent(const int _Array[_Rank])restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Array`  
 数组`_Rank`用于创建新的整数`extent`对象。  
  
 `_I`  
 范围的长度。  
  
 `_I0`  
 最重要的维的长度。  
  
 `_I1`  
 下一步-到-最高有效的维度的长度。  
  
 `_I2`  
 最低有效的维度的长度。  
  
 `_Other`  
 `extent`对象在其上的新`extent`基于对象。  
  
## <a name="remarks"></a>备注  
 无参数构造函数初始化`extent`具有三个级别的对象。  
  
 如果数组用于构造`extent`对象，该数组的长度必须匹配的秩`extent`对象。  
  
##  <a name="operator_mod_eq"></a>operator %= 

该元素除以一个数字时，计算范围中的每个元素的模数 （余数）。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 要查找其模数的数字。  
  
### <a name="return-value"></a>返回值  
 `extent` 对象。  
  
##  <a name="operator_star_eq"></a>运算符 * = 

返回由指定数量的范围对象中的每个元素的乘积。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 要相乘的数字。  
  
### <a name="return-value"></a>返回值  
 `extent` 对象。  
  
## <a name="operator_add"></a>operator + 

返回一个新`extent`对象是通过添加相应创建`index`和`extent`元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 `index`对象，其中包含要添加的元素。  
  
### <a name="return-value"></a>返回值  
 新的 `extent` 对象。  
  
##  <a name="operator_add_add"></a>operator + + 

递增扩展对象的每个元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator++() restrict(amp,cpu);    
extent<_Rank> operator++(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>返回值  
 对于前缀运算符，`extent`对象 (`*this`)。 后缀运算符，新`extent`对象。  
  
##  <a name="operator_add_eq"></a>运算符 + = 

将指定的数添加到扩展对象的每个元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 号、 索引或范围添加。  
  
### <a name="return-value"></a>返回值  
 生成的 `extent` 对象。  
  
##  <a name="operator_min"></a>operator- 

创建一个新`extent`对象中指定每个元素中的减去`index`对象中的相应元素从`extent`对象。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 `index`对象，其中包含要减去的元素。  
  
### <a name="return-value"></a>返回值  
 新的 `extent` 对象。  
  
##  <a name="operator_min_min"></a>运算符- 

递减范围对象中的每个元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator--() restrict(amp,cpu);    
extent<_Rank> operator--(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>返回值  
 对于前缀运算符，`extent`对象 (`*this`)。 后缀运算符，新`extent`对象。  
  
##  <a name="operator_div_eq"></a>/ = 运算符 

指定的数除以范围对象中的每个元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 要被除的数字。  
  
### <a name="return-value"></a>返回值  
 `extent` 对象。  
  
##  <a name="operator_min_eq"></a>operator = 

中减去指定的数目的范围对象的每个元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 要减去的数字。  
  
### <a name="return-value"></a>返回值  
 生成的 `extent` 对象。  
  
##  <a name="operator_eq"></a>运算符 = 

将另一个范围对象的内容复制到此。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `extent`从中进行复制的对象。  
  
### <a name="return-value"></a>返回值  
 对此引用`extent`对象。  
  
##  <a name="operator_at"></a>extent:: operator\[\] 
返回位于指定索引处的元素。  
  
### <a name="syntax"></a>语法  
  
```  
int operator[](unsigned int _Index) const restrict(amp,cpu);    
int& operator[](unsigned int _Index) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 一个介于 0 到减 1 的秩。  
  
### <a name="return-value"></a>返回值  
 位于指定索引处的元素。  
  
##  <a name="rank_constant"></a>级别 

将存储的扩展对象的秩。  
  
### <a name="syntax"></a>语法  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="size"></a>大小 

返回 `extent` 对象的总线性大小（以元素单位）。  
  
### <a name="syntax"></a>语法  

```  
unsigned int size() const restrict(amp,cpu);  
```  
  
## <a name="tile"></a>磁贴 

生成具有指定的图块维度的 tiled_extent 对象。

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```  
### <a name="parameters"></a>参数
`_Dim0`平铺范围中最重要的组成部分。
`_Dim1`平铺范围下一步-到-最高有效组件。
`_Dim2`平铺范围最低有效组件。


  
## <a name="see-also"></a>另请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
