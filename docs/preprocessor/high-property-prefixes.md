---
title: high_property_prefixes |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3932a7632b12120e722c5f375f4387e08f1853b
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809052"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes

**C + + 专用**

指定用于三个属性方法的备用前缀。

## <a name="syntax"></a>语法

```
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>参数

*GetPrefix*<br/>
前缀用于`propget`方法。

*PutPrefix*<br/>
前缀用于`propput`方法。

*PutRefPrefix*<br/>
前缀用于`propputref`方法。

## <a name="remarks"></a>备注

默认情况下，高级错误处理`propget`， `propput`，并`propputref`使用的前缀命名的成员函数公开方法`Get`， `Put`，和`PutRef`分别。

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)