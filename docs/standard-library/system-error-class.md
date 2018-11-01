---
title: system_error 类
ms.date: 11/04/2016
f1_keywords:
- system_error/std::system_error
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
ms.openlocfilehash: bad260e5372965c35517986da8feb2cfa3c0e1d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622256"
---
# <a name="systemerror-class"></a>system_error 类

表示为报告低级别系统错误而引发的所有异常的基类。

## <a name="syntax"></a>语法

```cpp
class system_error : public runtime_error {
public:
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

};
```

## <a name="remarks"></a>备注

由 [](../standard-library/exception-class.md) 类中的 `what` 返回的值根据 `_Message` 和 [error_code](../standard-library/error-code-class.md)（`code` 或 `error_code(_Errval, _Errcat)`）进行构造。

成员函数 `code` 返回存储的 [error_code](../standard-library/error-code-class.md) 对象。

## <a name="requirements"></a>要求

**标头：** \<system_error>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<system_error>](../standard-library/system-error.md)<br/>
