---
title: regex_traits&lt;char&gt; 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_traits<char>
dev_langs:
- C++
helpviewer_keywords:
- regex_traits<char> class
ms.assetid: ce95ebcd-3687-4ad5-bf1d-b89fdc633675
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2491fd14ccb7c165665cfb948836b7351dc907ce
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912896"
---
# <a name="regextraitsltchargt-class"></a>regex_traits&lt;char&gt; 类

用于 char 的 regex_traits 的专用化。

## <a name="syntax"></a>语法

```cpp
template <>
class regex_traits<char>
```

## <a name="remarks"></a>备注

此类是类型为 `char` 的元素的 [regex_traits](../standard-library/regex-traits-class.md) 模板类的显式专用化（以便它可以充分利用操作此类型对象的库函数）。

## <a name="requirements"></a>要求

**标头：**\<regex 1>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 类](../standard-library/regex-constants-class.md)<br/>
[regex_error 类](../standard-library/regex-error-class.md)<br/>
[\<regex> functions](../standard-library/regex-functions.md)<br/>
[regex_iterator 类](../standard-library/regex-iterator-class.md)<br/>
[\<regex> operators](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 类](../standard-library/regex-traits-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>
