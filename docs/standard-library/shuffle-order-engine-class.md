---
title: "shuffle_order_engine 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- shuffle_order_engine
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- shuffle_order_engine class
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 93c5721a4b651315bc4d67cc9d5a0cb7d2f852a3
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine 类
通过对从其基引擎中返回的值进行重新排序，生成随机序列。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Engine, size_t K>  
class shuffle_order_engine;  
```  
  
#### <a name="parameters"></a>参数  
 `Engine`  
 基引擎类型。  
  
 `K`  
 **表大小**。 缓冲区（表）中的元素数。 **前置条件**：`0 < K`  
  
## <a name="members"></a>成员  
  
||||  
|-|-|-|  
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|  
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|  
  
 有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>备注  
 此模板类描述了通过对其基引擎返回的值进行重新排序来产生值的引擎适配器。 每个构造函数都将使用由基引擎返回的 `K` 值填充内部表，请求一个值后，将从该表中选择一个随机元素。  
  
## <a name="requirements"></a>要求  
 **标头：**\<random>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [\<random>](../standard-library/random.md)


