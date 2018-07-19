---
title: bad_alloc 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- new/std::bad_alloc
dev_langs:
- C++
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e76bd39477c92d075f1dba8cf14b912c0f616e0
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955905"
---
# <a name="badalloc-class"></a>bad_alloc 类

该类描述引发的异常以指示分配请求未成功。

## <a name="syntax"></a>语法

```cpp
class bad_alloc : public exception {
    bad_alloc();
virtual ~bad_alloc();

};
```

## <a name="remarks"></a>备注

返回的值`what`是实现定义的 C 字符串。 无成员函数引发任何异常。

## <a name="requirements"></a>要求

**标头：**\<new>

**命名空间：** std

## <a name="example"></a>示例

```cpp
// bad_alloc.cpp
// compile with: /EHsc
#include<new>
#include<iostream>
using namespace std;

int main() {
   char* ptr;
   try {
      ptr = new char[(~unsigned int((int)0)/2) - 1];
      delete[] ptr;
   }
   catch( bad_alloc &ba) {
      cout << ba.what( ) << endl;
   }
}
```

## <a name="sample-output"></a>示例输出

```Output
bad allocation
```

## <a name="requirements"></a>要求

**标头：**\<new>

## <a name="see-also"></a>请参阅

[exception 类](../standard-library/exception-class.md) [c + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
