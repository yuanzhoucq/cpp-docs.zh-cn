---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 70e05ad734fa49ba8cb96e4bf83bc05b99c5f55c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246527"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

包含标准 C 库标头\<stdlib.h >，并将添加到关联的名称`std`命名空间。 包括此标头中声明 C 标准库标头中使用外部链接声明的名称将确保`std`命名空间。

> [!NOTE]
> \<在 stdlib.h > 不包括类型**wchar_t**。

## <a name="requirements"></a>要求

**标头**: \<cstdlib >

**命名空间：** std

## <a name="namespace-and-macros"></a>Namespace 和宏

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

## <a name="exposition-only-functions"></a>阐述仅起作用

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>启动和终止函数

|函数|描述|
|-|-|
|[_Exit](#_exit)|无需使用析构函数或已注册的函数将终止程序。|
|[abort](#abort)|而无需使用析构函数将终止程序。|
|[atexit](#atexit)|程序终止的注册函数。|
|[exit](#exit)|销毁线程和静态存储，然后返回控件的对象。|
|[at_quick_exit](#at_quick_exit)|寄存器不含程序终止的参数的函数。|
|[quick_exit](#quick_exit)|与程序终止的保留对象的注册函数。|
|[getenv](#getenv)|请参阅 C 标准库参考。|
|[system](#system)|请参阅 C 标准库参考。|

### <a name="_exit"></a> _Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>备注

无需执行的自动对象、 线程或静态存储持续时间的析构函数和调用传递给函数终止程序`atexit()`。 该函数`_Exit`是安全的信号。

### <a name="abort"></a> 中止

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>备注

无需执行的自动对象、 线程或静态存储持续时间的析构函数和调用传递给函数终止程序`atexit()`。 该函数`abort`是安全的信号。

### <a name="at_quick_exit"></a> at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>返回值

如果注册成功则为零、 非零值; 如果它无法正常工作。

#### <a name="remarks"></a>备注

`at_quick_exit()`函数注册由所指向的函数*func*调用不带参数时`quick_exit`调用。 它具有未指定是否调用`at_quick_exit()`之前对所有调用未按预期进行`quick_exit`将会成功和`at_quick_exit()`函数不会引入数据争用。 注册的顺序可能是不确定如果`at_quick_exit`从多个与一个线程，因为调用了`at_quick_exit`注册是不同于`atexit`注册，可能需要应用程序调用具有这两个注册函数相同的参数。 实现应支持至少 32 函数的注册。

### <a name="atexit"></a> atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>备注

`atexit()`函数注册由所指向的函数*func*而不使用参数在正常程序终止时调用。 它具有未指定是否调用`atexit()`调用之前未按预期进行`exit()`将会成功和`atexit()`函数不会引入数据争用。实现应支持至少 32 函数的注册。

#### <a name="return-value"></a>返回值

如果注册成功，如果失败，非零值，则返回零。

### <a name="exit"></a> 退出

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>备注

首先，使用线程存储持续时间对象，并关联与当前线程被破坏。

接下来，具有静态存储持续时间的对象将销毁，并通过调用注册函数`atexit`调用。 调用不会销毁自动对象`exit()`。 如果控件将已注册的函数调用的则`exit`函数不会提供的处理程序引发的异常，因为`std::terminate()`应被调用。 每次注册时，将为调用函数。 具有自动存储持续时间的对象在程序中的主函数不包含自动对象和执行对调用销毁`exit()`。 通过引发异常捕获到 main 中，可以将控制转移直接到此类主要函数。

接下来，所有打开的 C 流 (如通过中声明的函数签名<cstdio>) 未写入缓冲的数据与 C 流都将关闭，为刷新，所有打开的所有文件的创建和调用`tmpfile()`删除。

最后，将控件返回给主机环境。 如果状态为零或 EXIT_SUCCESS，则返回的状态成功终止的实现定义窗体。 如果状态为 EXIT_FAILURE，则返回的状态不成功终止的实现定义窗体。 否则返回的状态是实现定义的。

### <a name="getenv"></a> getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a> quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>备注

通过调用注册函数`at_quick_exit`只不过后任何以前已注册的函数已调用在其注册的时，应调用的函数为其注册的相反顺序调用。 调用应不会销毁对象`quick_exit`。 如果控件将已注册的函数调用的则`quick_exit`函数不会提供的处理程序引发的异常，因为`std::terminate()`应被调用。 通过注册函数`at_quick_exit`调用的线程调用`quick_exit`，可以是不同的线程不是一个注册它，因此注册函数不应依赖于具有线程存储持续时间的对象的标识。 调用已注册的函数后`quick_exit`应调用`_Exit(status)`。 标准文件缓冲区不会刷新。 该函数`quick_exit`是安全的信号时向注册函数`at_quick_exit`是。

### <a name="system"></a> 系统

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>内存分配函数

```cpp
void* aligned_alloc(size_t alignment, size_t size);
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
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

#### <a name="remarks"></a>备注

这些函数具有 C 标准库中指定的语义。

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>多字节 / 宽字符串和字符转换函数

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

## <a name="low-quality-random-number-generation-functions"></a>低质量随机数字生成函数

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
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>备注

这些函数具有 C 标准库中指定的语义。

## <a name="functions"></a>函数

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
