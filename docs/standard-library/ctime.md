---
title: '&lt;ctime&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ctime>
- std::<ctime>
helpviewer_keywords:
- ctime header
ms.assetid: c1f7d4a4-4bfe-4e35-92cb-f63dbd3c39a8
ms.openlocfilehash: f4bdb8fa30c44a6eaa83f53624c5bd43bd235261
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449378"
---
# <a name="ltctimegt"></a>&lt;ctime&gt;

包含标准 C 库标头 \<time.h> 并将关联名称添加到 `std` 命名空间。

## <a name="syntax"></a>语法

```cpp
#include <ctime>
```

## <a name="remarks"></a>备注

包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。

## <a name="constants"></a>常量

```cpp
#define NULL
#define CLOCKS_PER_SEC
#define TIME_UTC

namespace std {
    using size_t = see below;
    using clock_t = see below ;
    using time_t = see below ;
}
```
    
## <a name="structures"></a>结构
    
```cpp
struct timespec;
struct tm;
```
    
## <a name="functions"></a>函数

```cpp
clock_t clock();
double difftime(time_t time1, time_t time0);
time_t mktime(struct tm* timeptr);
time_t time(time_t* timer);
int timespec_get(timespec* ts, int base);
char* asctime(const struct tm* timeptr);
char* ctime(const time_t* timer);
struct tm* gmtime(const time_t* timer);
struct tm* localtime(const time_t* timer);
size_t strftime(char* s, size_t maxsize, const char* format, const struct tm* timeptr);
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
