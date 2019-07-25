---
title: future_error 类
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: ed3f9d63c45d0e185e3e1476094736d132822173
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447351"
---
# <a name="futureerror-class"></a>future_error 类

描述可由管理 [future](../standard-library/future-class.md) 对象的类型方法引发的异常对象。

## <a name="syntax"></a>语法

```cpp
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```

## <a name="requirements"></a>要求

**标头:** \<未来 >

**命名空间：** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[logic_error 类](../standard-library/logic-error-class.md)\
[error_code 类](../standard-library/error-code-class.md)
