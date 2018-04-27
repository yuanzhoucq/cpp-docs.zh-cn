---
title: identity 结构 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- utility/std::identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 991333f279053d19ec27fda86ea0bf769371fd90
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="identity-structure"></a>identity 结构

一个将类型定义作为模板参数提供的结构。

## <a name="syntax"></a>语法

```cpp
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };
```
### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`left`|要识别的值。|

## <a name="remarks"></a>备注

此类包含公共类型定义 `type`，其与模板参数 Type 相同。 它与模板函数 [forward](../standard-library/utility-functions.md#forward) 结合使用，从而确保函数参数具有所需的类型。

为与旧版代码兼容，此类还定义了 identity 函数 `operator()`，该函数会返回其参数 `left`。

## <a name="requirements"></a>要求

**标头：**\<utility>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<utility>](../standard-library/utility.md)<br/>
