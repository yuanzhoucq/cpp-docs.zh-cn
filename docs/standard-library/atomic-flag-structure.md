---
title: "atomic_flag 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs:
- C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8774bcc4b95e2b5c0160843100405f33010b98b6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="atomicflag-structure"></a>atomic_flag 结构
描述以原子方式设置并清除 `bool` 标志的对象。 对原子标志执行的操作始终是无锁的。  
  
## <a name="syntax"></a>语法  
  
```
struct atomic_flag;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[clear](#clear)|将存储的标志设置为 `false`。|  
|[test_and_set](#test_and_set)|将存储的标志设置为 `true` 并返回初始标志值。|  
  
## <a name="remarks"></a>备注  
 `atomic_flag` 对象可传递给非成员函数 [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)、[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)、[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) 和 [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)。 可使用值 `ATOMIC_FLAG_INIT` 对其进行初始化。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<原子 >  
  
 **命名空间：** std  
  
##  <a name="clear"></a>  atomic_flag::clear
 将存储在 `*this` 中的 `bool` 标志设置为 `false`（限于指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 约束）。  
  
```
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。  
  
##  <a name="test_and_set"></a>  atomic_flag::test_and_set
 将存储在 `*this` 中的 `bool` 标志设置为 `true`（限于指定的 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 约束）。  
  
```
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum)。  
  
### <a name="return-value"></a>返回值  
 存储在 `*this` 中的标志的初始值。  
  
## <a name="see-also"></a>请参阅  
 [\<atomic>](../standard-library/atomic.md)



