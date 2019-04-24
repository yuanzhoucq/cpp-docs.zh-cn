---
title: future_error 类
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: 2b3f754c0ceb7384d99c6a657de214d30aca24b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159751"
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

**标头：** \<将来 >

**命名空间：** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[logic_error 类](../standard-library/logic-error-class.md)<br/>
[error_code 类](../standard-library/error-code-class.md)<br/>
