---
title: "extent 类 (c + + AMP) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::extent
dev_langs:
- C++
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
caps.latest.revision: 19
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
ms.openlocfilehash: 8aa89b882ed075a8cdf0166d43fde1a5bfe7683d
ms.lasthandoff: 02/24/2017

---
# <a name="extent-class-c-amp"></a>extent 类 (C++ AMP)
表示一个向量*N*指定的边界的整数值*N*-具有 0 来源的维空间。 对向量中的值按照从最重要到最不重要的顺序排列。  
  
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
  
|名称|说明|  
|----------|-----------------|  
|[extent 构造函数](#ctor)|初始化 `extent` 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[包含方法](#contains)|验证指定`extent`对象具有指定的秩。|  
|[size 方法](#size)|返回 （以元素单位） 的范围内的总线性大小。|  
|[平铺方法](#tile)|生成`tiled_extent`指定维度与给定的磁贴扩展盘区的对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[operator-运算符](#operator_min)|返回一个新`extent`减去创建对象`index`从相应的元素`extent`元素。|  
|[运算符-运算符](#operator_min_min)|递减的每个元素`extent`对象。|  
|[operator %= 运算符](#operator_mod_eq)|计算中每个元素的模数 （余数）`extent`对象时某个数除该元素。|  
|[运算符 * = 运算符](#operator_star_eq)|将相乘的每个元素`extent`由很多对象。|  
|[运算符 / = 运算符](#operator_min_eq)|将划分的每个元素`extent`由很多对象。|  
|[extent:: operator\[\]](#operator_at)|返回位于指定索引处的元素。|  
|[operator + 运算符](#operator_add)|返回一个新`extent`创建通过添加相应的对象`index`和`extent`元素。|  
|[operator + + 运算符](#operator_add_add)|递增的每个元素`extent`对象。|  
|[运算符 + = 运算符](#operator_add_eq)|将指定的数加到的每个元素`extent`对象。|  
|[运算符 = 运算符](#operator_eq)|将另一个的内容复制`extent`到此对象。|  
|[operator-= 运算符](#operator_min_eq)|从的每个元素指定的数中减去`extent`对象。|  

  
### <a name="public-constants"></a>公共常量  
  
|名称|描述|  
|----------|-----------------|  
|[rank 常量](#rank)|获取的秩`extent`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `extent`  


## <a name="a-namecontainsa-contains"></a><a name="contains"></a>包含 

指示是否指定[索引](index-class.md)范围对象中包含值。  
  
### <a name="syntax"></a>语法  
  
```  
bool contains(const index<rank>& _Index) const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 `index`要测试其值。  
  
### <a name="return-value"></a>返回值  
 `true`如果指定`index`值包含在`extent`对象; 否则为`false`。  
  
##  <a name="a-namectora-extent"></a><a name="ctor"></a>扩展盘区 

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
 一个数组`_Rank`用于创建新的整数`extent`对象。  
  
 `_I`  
 此扩展盘区的长度。  
  
 `_I0`  
 最重要的维的长度。  
  
 `_I1`  
 下一步-到-最高有效的维的长度。  
  
 `_I2`  
 最不重要的维的长度。  
  
 `_Other`  
 `extent`在其上的对象的新`extent`基于对象。  
  
## <a name="remarks"></a>备注  
 无参数构造函数初始化`extent`的排名为&3; 的对象。  
  
 如果使用一个数组来构造`extent`对象，该数组的长度必须匹配的秩不匹配`extent`对象。  
  
##  <a name="a-nameoperatormodeqa-operator"></a><a name="operator_mod_eq"></a>operator %= 

该元素被某个数除时将计算范围中的每个元素的模数 （余数）。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 要查找其模数的数字。  
  
### <a name="return-value"></a>返回值  
 `extent` 对象。  
  
##  <a name="a-nameoperatorstareqa-operator"></a><a name="operator_star_eq"></a>运算符 * = 

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
  
## <a name="a-nameoperatoradda-operator"></a><a name="operator_add"></a>operator + 

返回一个新`extent`创建通过添加相应的对象`index`和`extent`元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 `index`对象，其中包含要添加的元素。  
  
### <a name="return-value"></a>返回值  
 新的 `extent` 对象。  
  
##  <a name="a-nameoperatoraddadda-operator"></a><a name="operator_add_add"></a>operator + + 

递增区对象的每个元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator++() restrict(amp,cpu);    
extent<_Rank> operator++(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>返回值  
 为前缀运算符`extent`对象 (`*this`)。 后缀运算符新`extent`对象。  
  
##  <a name="a-nameoperatoraddeqa-operator"></a><a name="operator_add_eq"></a>operator + = 

将指定的数字与扩展对象的每个元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 数字、 索引或范围内来添加。  
  
### <a name="return-value"></a>返回值  
 生成的 `extent` 对象。  
  
##  <a name="a-nameoperatormina-operator-"></a><a name="operator_min"></a>operator- 

创建一个新`extent`对象中指定每个元素中的减去`index`对象中的相应元素`extent`对象。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 `index`对象，其中包含要减去的元素。  
  
### <a name="return-value"></a>返回值  
 新的 `extent` 对象。  
  
##  <a name="a-nameoperatorminmina-operator--"></a><a name="operator_min_min"></a>操作符 — 

递减范围对象中的每个元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator--() restrict(amp,cpu);    
extent<_Rank> operator--(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>返回值  
 为前缀运算符`extent`对象 (`*this`)。 后缀运算符新`extent`对象。  
  
##  <a name="a-nameoperatordiveqa-operator"></a><a name="operator_div_eq"></a>/ = 运算符 

除以指定数量的扩展对象中的每个元素。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 要除以的数字。  
  
### <a name="return-value"></a>返回值  
 `extent` 对象。  
  
##  <a name="a-nameoperatormineqa-operator-"></a><a name="operator_min_eq"></a>运算符 = 

从扩展对象的每个元素指定的数中减去。  
  
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
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>运算符 = 

将范围的另一个对象的内容复制到此。  
  
### <a name="syntax"></a>语法  
  
```  
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `extent`从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 参考这`extent`对象。  
  
##  <a name="a-nameoperatorata-extentoperator-"></a><a name="operator_at"></a>extent:: operator\[\] 
返回位于指定索引处的元素。  
  
### <a name="syntax"></a>语法  
  
```  
int operator[](unsigned int _Index) const restrict(amp,cpu);    
int& operator[](unsigned int _Index) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 一个介于 0 到减 1 的排名。  
  
### <a name="return-value"></a>返回值  
 位于指定索引处的元素。  
  
##  <a name="a-namerankconstanta-rank"></a><a name="rank_constant"></a>排名 

将存储的扩展对象的秩。  
  
### <a name="syntax"></a>语法  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-namesizea-size"></a><a name="size"></a>大小 

返回 `extent` 对象的总线性大小（以元素单位）。  
  
### <a name="syntax"></a>语法  

```  
unsigned int size() const restrict(amp,cpu);  
```  
  
## <a name="a-nametilea-tile"></a><a name="tile"></a>磁贴 

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
`_Dim2`平铺范围中最不重要的组成部分。


  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

