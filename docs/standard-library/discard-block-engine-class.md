---
title: "discard_block_engine 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: random/std::discard_block_engine
dev_langs: C++
helpviewer_keywords: discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ca21ef820c4dfe713a5a9b0c969ac0b14e3efe01
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="discardblockengine-class"></a>discard_block_engine 类
通过丢弃由其基引擎返回的值，生成随机序列。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Engine, size_t P, size_t R>  
class discard_block_engine;  
```  
  
#### <a name="parameters"></a>参数  
 `Engine`  
 基引擎类型。  
  
 `P`  
 **块大小**。 每个块中的值数。  
  
 `R`  
 **已使用的块**。 已使用的每个块中的值数。 丢弃剩余部分 ( `P` - `R`)。 **前提条件**：`0 < R ≤ P`  
  
## <a name="members"></a>成员  
  
||||  
|-|-|-|  
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|  
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|  
  
 有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>备注  
 此模板类描述了通过弃用由其基引擎返回的一些值来产生值的引擎适配器。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<random>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [\<random>](../standard-library/random.md)

