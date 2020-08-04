---
title: logic_error 类
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::logic_error
helpviewer_keywords:
- logic_error class
ms.assetid: b290d73d-94e1-4288-af86-2bb5d71f677a
ms.openlocfilehash: b94f7f4c2482f0317e37c6f4bf3618b91a175147
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521182"
---
# <a name="logic_error-class"></a>logic_error 类

此类用作引发报告执行程序前大概可检测的错误（例如，违反逻辑前提条件）的所有异常的基类。

## <a name="syntax"></a>语法

```cpp
class logic_error : public exception {
public:
    explicit logic_error(const string& message);

    explicit logic_error(const char *message);

};
```

## <a name="remarks"></a>备注

返回的值 `what()` 是的副本 `message.data()` 。 有关详细信息，请参阅 [`what`](../standard-library/exception-class.md) 和 [`data`](../standard-library/basic-string-class.md#data)。

## <a name="example"></a>示例

```cpp
// logic_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;

int main( )
{
   try
   {
      throw logic_error( "logic error" );
   }
   catch ( exception &e )
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
```

```Output
Caught: logic error
Type: class std::logic_error
```

## <a name="requirements"></a>要求

**标头：**\<stdexcept>

**命名空间:** std

## <a name="see-also"></a>请参阅

[exception 类](../standard-library/exception-class.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
