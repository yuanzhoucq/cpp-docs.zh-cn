---
title: '&lt;cstring&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstring>
helpviewer_keywords:
- <cstring> header
- cstring header
ms.assetid: d665429f-5d39-4712-9c0a-68c8abcc3536
ms.openlocfilehash: cc6821d63a42d498347745bb7a96c838fc634415
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246620"
---
# <a name="ltcstringgt"></a>&lt;cstring&gt;

包含标准 C 库标头 \<string.h> 并将关联名称添加到 `std` 命名空间。

## <a name="syntax"></a>语法

```cpp
#include <cstring>
```

## <a name="remarks"></a>备注

包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。

## <a name="constants"></a>常量

```cpp
namespace std {
    using size_t = see below;
}

#define NULL
```

## <a name="functions"></a>函数

```cpp
void* memcpy(void* s1, const void* s2, size_t n);
void* memmove(void* s1, const void* s2, size_t n);
char* strcpy(char* s1, const char* s2);
char* strncpy(char* s1, const char* s2, size_t n);
char* strcat(char* s1, const char* s2);
char* strncat(char* s1, const char* s2, size_t n);
int memcmp(const void* s1, const void* s2, size_t n);
int strcmp(const char* s1, const char* s2);
int strcoll(const char* s1, const char* s2);
int strncmp(const char* s1, const char* s2, size_t n);
size_t strxfrm(char* s1, const char* s2, size_t n);
const void* memchr(const void* s, int c, size_t n); // see 20.2
void* memchr(void* s, int c, size_t n) // see 20.2
const char* strchr(const char* s, int c) // see 20.2
char* strchr(char* s, int c) // see 20.2
size_t strcspn(const char* s1, const char* s2);
const char* strpbrk(const char* s1, const char* s2) // see 20.2
char* strpbrk(char* s1, const char* s2) // see 20.2
const char* strrchr(const char* s, int c) // see 20.2
char* strrchr(char* s, int c) // see 20.2
size_t strspn(const char* s1, const char* s2);
const char* strstr(const char* s1, const char* s2) // see 20.2
char* strstr(char* s1, const char* s2) // see 20.2
char* strtok(char* s1, const char* s2);
void* memset(void* s, int c, size_t n);
char* strerror(int errnum);
size_t strlen(const char* s);
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
