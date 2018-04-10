---
title: short_vector 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- short_vector
- AMP_SHORT_VECTORS/short_vector
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector::short_vector Constructor
dev_langs:
- C++
ms.assetid: e4f50b8f-1150-437d-b58c-79c5fb883708
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d71ef4577845319bf66ef51e92afae7907526008
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/10/2018
---
# <a name="shortvector-structure"></a>short_vector 结构
short_vector 提供可广泛用于短矢量编程的元编程定义。  
  
## <a name="syntax"></a>语法  
  
```  
template<
    typename _Scalar_type,  
    int _Size  
>  
struct short_vector;  
template<>  
struct short_vector<unsigned int, 1>;  
template<>  
struct short_vector<unsigned int, 2>;  
template<>  
struct short_vector<unsigned int, 3>;  
template<>  
struct short_vector<unsigned int, 4>;  
template<>  
struct short_vector<int, 1>;  
template<>  
struct short_vector<int, 2>;  
template<>  
struct short_vector<int, 3>;  
template<>  
struct short_vector<int, 4>;  
template<>  
struct short_vector<float, 1>;  
template<>  
struct short_vector<float, 2>;  
template<>  
struct short_vector<float, 3>;  
template<>  
struct short_vector<float, 4>;  
template<>  
struct short_vector<unorm, 1>;  
template<>  
struct short_vector<unorm, 2>;  
template<>  
struct short_vector<unorm, 3>;  
template<>  
struct short_vector<unorm, 4>;  
template<>  
struct short_vector<norm, 1>;  
template<>  
struct short_vector<norm, 2>;  
template<>  
struct short_vector<norm, 3>;  
template<>  
struct short_vector<norm, 4>;  
template<>  
struct short_vector<double, 1>;  
template<>  
struct short_vector<double, 2>;  
template<>  
struct short_vector<double, 3>;  
template<>  
struct short_vector<double, 4>;  
```  
  
#### <a name="parameters"></a>参数  
 `_Scalar_type`  
 `_Size`  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`type`||  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[short_vector:: short_vector 构造函数](#ctor)||  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `short_vector`  
  
## <a name="requirements"></a>要求  
 **标头：** amp_short_vectors.h  
  
 **Namespace:** concurrency:: graphics  
  
##  <a name="ctor"></a>  short_vector:: short_vector 构造函数  
  
```  
short_vector();
```  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
