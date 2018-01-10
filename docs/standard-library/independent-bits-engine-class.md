---
title: "independent_bits_engine 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: random/std::independent_bits_engine
dev_langs: C++
helpviewer_keywords: independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ec9a4b9beac581df0060f239916c06b8b6191de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="independentbitsengine-class"></a>independent_bits_engine 类
通过再次从其基引擎返回的值中打包位，生成具有指定位数的随机数字序列。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Engine, size_t W, class UIntType>  
class independent_bits_engine;  
```  
  
### <a name="parameters"></a>参数  
 `Engine`  
 基引擎类型。  
  
 `W`  
 **字大小**。 生成的每个数字的大小（以字节为单位）。 **前提条件**：`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `UIntType`  
 无符号的整数结果类型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="members"></a>成员  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>备注  
 此模板类描述了*引擎适配器*，该引擎适配器通过再次打包其基引擎返回的值中的位来产生 `W` 位值。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<random>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [\<random>](../standard-library/random.md)

