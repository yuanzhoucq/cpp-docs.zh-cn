---
title: raw_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: 23250b524fdaa2181c8e28229ccec680ffdae715
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033250"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes

**C++ 专用**

指定用于三个属性方法的备用前缀。

## <a name="syntax"></a>语法

```
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>参数

*GetPrefix*<br/>
前缀用于`propget`方法。

*PutPrefix*<br/>
前缀用于`propput`方法。

*PutRefPrefix*<br/>
前缀用于`propputref`方法。

## <a name="remarks"></a>备注

默认情况下，低级别`propget`， `propput`，并`propputref`具有前缀的命名的成员函数公开方法**get_**， **put_**，和**putref_** 分别。 这些前缀与在 MIDL 生成的标头文件中使用的名称兼容。

**结束 C++ 专用**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)