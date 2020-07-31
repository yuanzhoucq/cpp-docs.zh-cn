---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 1b20e13a43c5d223332af70a91e096cedc284a43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230047"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

包括 C 标准库标头 \<stdlib.h> 并将关联名称添加到 `std` 命名空间。 包括此标头可确保在命名空间中声明使用 C 标准库标头中的外部链接声明的名称 `std` 。

> [!NOTE]
> \<stdlib.h>不包括类型 **`wchar_t`** 。

## <a name="requirements"></a>要求

**标头**：\<cstdlib>

**命名空间:** std

## <a name="namespace-and-macros"></a>命名空间和宏

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>仅处于阐释函数

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>开始和终止功能

|函数|说明|
|-|-|
|[_Exit](#_exit)|终止程序，而不使用析构函数或已注册的函数。|
|[中止](#abort)|终止程序，而不使用析构函数。|
|[atexit](#atexit)|注册程序终止函数。|
|[exit](#exit)|用线程和静态存储销毁对象，然后返回 control。|
|[at_quick_exit](#at_quick_exit)|在程序终止时注册不带参数的函数。|
|[quick_exit](#quick_exit)|用保留的对象注册程序终止函数。|
|[getenv](#getenv)|请参阅 C 标准库参考。|
|[系统](#system)|请参阅 C 标准库参考。|

### <a name="_exit"></a><a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>备注

如果没有为自动、线程或静态存储持续时间的对象执行析构函数，并且没有调用传递到的函数，程序将终止 `atexit()` 。 函数的 `_Exit` 信号安全。

### <a name="abort"></a><a name="abort"></a>中断

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>备注

如果没有为自动、线程或静态存储持续时间的对象执行析构函数，并且没有调用传递到的函数，程序将终止 `atexit()` 。 函数的 `abort` 信号安全。

### <a name="at_quick_exit"></a><a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>返回值

如果注册成功，则为零; 如果失败，则为非零。

#### <a name="remarks"></a>备注

`at_quick_exit()`函数将注册函数*func*，调用时，该函数不带参数调用 `quick_exit` 。 对的调用 `at_quick_exit()` 在对的所有调用都 `quick_exit` 不会成功之前不会发生。 `at_quick_exit()`函数不会引入数据争用。 如果从多个线程调用，则注册顺序可能不确定 `at_quick_exit` 。 由于 `at_quick_exit` 注册不同于 `atexit` 注册，因此应用程序可能需要使用相同的参数调用这两个注册函数。 MSVC 支持至少32个函数的注册。

### <a name="atexit"></a><a name="atexit"></a>atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>备注

`atexit()`函数在正常程序终止时注册要*func*在没有参数的情况下调用的函数所指向的函数。 对的调用在 `atexit()` 调用可能失败之前不会 `exit()` 发生。 `atexit()`函数不会引入数据争用。

#### <a name="return-value"></a>返回值

如果注册成功，则返回零; 如果失败，则返回非零值。

### <a name="exit"></a><a name="exit"></a>离开

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>备注

首先，将销毁线程存储持续时间和与当前线程关联的对象。

接下来，将销毁具有静态存储持续时间的对象，并调用通过调用注册的函数 `atexit` 。 调用时，自动对象不会 `exit()` 被销毁。 如果控件离开由调用的已注册函数 `exit` ，因为函数不提供引发的异常的处理程序， `std::terminate()` 则会调用。 每次注册函数时，都会调用一次函数。 具有自动存储持续时间的对象全部在其 `main` 函数不包含自动对象并执行对的程序中销毁 `exit()` 。 控件可以通过引发中捕获的异常直接传输到此类 `main` 函数 `main` 。

接下来，将刷新所有打开的 C 流（如中用声明的函数签名经过调谐 \<cstdio> ），并关闭所有打开的 c 流，并删除通过调用创建的所有文件 `tmpfile()` 。

最后，控制将返回到主机环境。 如果*状态*为零或 EXIT_SUCCESS，则返回实现定义形式的状态成功终止。 MSVC 返回的值为零。 如果*状态*为 "EXIT_FAILURE"，则 MSVC 返回的值为3。 否则，MSVC 将返回*status*参数值。

### <a name="getenv"></a><a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a><a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>备注

通常，通过调用注册的函数 `at_quick_exit` 将按其注册的相反顺序调用。 此顺序并不适用于已调用其他已注册函数后注册的函数。 调用时不会销毁任何对象 `quick_exit` 。 如果控件离开由调用的已注册函数 `quick_exit` ，因为函数不提供引发的异常的处理程序， `std::terminate()` 则会调用。 通过注册的函数 `at_quick_exit` 由调用的线程调用 `quick_exit` ，后者可以是与注册它的线程不同的线程。 这意味着注册的函数不应依赖于具有线程存储持续时间的对象的标识。 调用注册的函数后， `quick_exit` 调用 `_Exit(status)` 。 标准文件缓冲区不会刷新。 `quick_exit`当向注册的函数为时，函数为信号安全函数 `at_quick_exit` 。

### <a name="system"></a><a name="system"></a>主板

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>内存分配函数

```cpp
// void* aligned_alloc(size_t alignment, size_t size); // Unsupported in MSVC
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
```

### <a name="remarks"></a>备注

这些函数具有 C 标准库中指定的语义。 MSVC 不支持 `aligned_alloc` 函数。 C11 指定的 `aligned_alloc()` 方式与的 Microsoft 实现 `free()` （即， `free()` 必须能够处理高度对齐的分配）不兼容。

## <a name="numeric-string-conversions"></a>数值字符串转换

```cpp
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

### <a name="remarks"></a>备注

这些函数具有 C 标准库中指定的语义。

## <a name="multibyte--wide-string-and-character-conversion-functions"></a>多字节/宽字符串和字符转换函数

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>备注

这些函数具有 C 标准库中指定的语义。

## <a name="algorithm-functions"></a>算法函数

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>备注

这些函数具有 C 标准库中指定的语义。

## <a name="low-quality-random-number-generation-functions"></a>低质量随机数生成函数

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>备注

这些函数具有 C 标准库中指定的语义。

## <a name="absolute-values"></a>绝对值

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
```

### <a name="remarks"></a>备注

这些函数具有 C 标准库中指定的语义。

## <a name="integer-division"></a>整数除法

```cpp
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>备注

这些函数具有 C 标准库中指定的语义。

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
