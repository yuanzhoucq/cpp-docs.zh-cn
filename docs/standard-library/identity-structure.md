---
title: identity 结构
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 722eb9c0579d0c07765434127d0a7c43718fbc37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615509"
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
|*left*|要识别的值。|

## <a name="remarks"></a>备注

此类包含公共类型定义 `type`，其与模板参数 Type 相同。 它与模板函数 [forward](../standard-library/utility-functions.md#forward) 结合使用，从而确保函数参数具有所需的类型。

为了与较旧的代码兼容，该类还定义了 identity 函数`operator()`这会返回其自变量*左*。

## <a name="requirements"></a>要求

**标头：**\<utility>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<utility>](../standard-library/utility.md)<br/>
