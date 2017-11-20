---
title: "to_vector 函数 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Windows::Foundation::Collections::to_vector
dev_langs: C++
helpviewer_keywords: to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
caps.latest.revision: "3"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 2f9df89c398e943af3c422b7e025ad371a3e8285
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="tovector-function"></a>to_vector 函数
返回 `std::vector` ，其值与指定 IVector 或 IVectorView 参数所代表的集合相同。  
  
## <a name="syntax"></a>语法  
  
```  
template <typename T>  
inline ::std::vector<T> to_vector(IVector<T>^ v); 
 
template <typename T>  
inline ::std::vector<T> to_vector(IVectorView<T>^ v);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 模板类型参数。  
  
 `v`  
 提供对基础 Vector 或 VectorView 对象访问的 IVector 或 IVectorView 接口。  
  
### <a name="return-value"></a>返回值  
  
### <a name="requirements"></a>要求  
 **标头：** collection.h  
  
 **命名空间：** Windows::Foundation::Collections  
  
## <a name="see-also"></a>另请参阅  
 [Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)