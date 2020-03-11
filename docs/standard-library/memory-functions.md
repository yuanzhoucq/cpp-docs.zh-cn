---
title: '&lt;memory&gt; 函数'
ms.date: 08/05/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::default_delete
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
- memory/std::get_temporary_buffer
- memory/std::return_temporary_buffer
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.openlocfilehash: 2aceb96fcda49df8a1fd40a1bd8011170dccd8ef
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856678"
---
# <a name="ltmemorygt-functions"></a>&lt;memory&gt; 函数

## <a name="addressof"></a>addressof

获取对象的实际地址。

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>parameters

*value*\
要获取其实际地址的对象或函数。

### <a name="return-value"></a>返回值

*值*引用的对象或函数的实际地址，即使存在重载的 `operator&()` 也是如此。

### <a name="remarks"></a>备注

## <a name="align"></a>垂直

将给定大小的存储空间（按给定的对齐规范对齐）放入给定存储的第一个可能地址。

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>parameters

*对齐*\
要尝试的对齐边界。

size\
对齐存储的大小（以字节为单位）。

*ptr*\
要使用的可用连续存储池的起始地址。 此参数也是 output 参数，如果对齐成功，则设置为包含新的起始地址。 如果 `align()` 不成功，则不修改此参数。

*空间*\
供 `align()` 用于创建对齐存储的总空间。 此参数还是输出参数，并包含存储缓冲区中在减去对齐存储和任何关联系统开销后剩余的调整空间。

如果 `align()` 不成功，则不修改此参数。

### <a name="return-value"></a>返回值

如果所请求的对齐缓冲区无法放入可用空间，则为 null 指针;否则为*ptr*的新值。

### <a name="remarks"></a>备注

使用修改的*ptr*和*空间*参数，可以在同一缓冲区上重复调用 `align()`，可能会有不同的值用于*对齐*和*调整大小*。 下面的代码片段演示 `align()` 的一种用法。

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a>allocate_shared

使用指定的分配器创建对给定类型分配和构造的对象的[shared_ptr](shared-ptr-class.md) 。 返回 `shared_ptr`。

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>parameters

*分配*\
用于创建对象的分配器。

*args*\
成为对象的零个或更多自变量。

### <a name="remarks"></a>备注

函数创建对象 `shared_ptr<T>`，该指针指向 `T(args...)`，它*由分配分配和构造。*

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a>atomic_exchange

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a>atomic_load

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a>atomic_load_explicit

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a>atomic_store

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a>atomic_store_explicit

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a>const_pointer_cast

Const 强制转换为[shared_ptr](shared-ptr-class.md)。

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>parameters

*T*\
由返回的共享指针控制的类型。

*其他*\
由自变量共享指针控制的类型。

*sp*\
自变量共享指针。

### <a name="remarks"></a>备注

如果 `const_cast<T*>(sp.get())` 返回空指针，则模板函数将返回空的 `shared_ptr` 对象;否则，它将返回拥有*sp*拥有的资源的 `shared_ptr<T>` 对象。 表达式 `const_cast<T*>(sp.get())` 必须有效。

### <a name="example"></a>示例

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

    *sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a>declare_no_pointers

通知垃圾回收器：通过基地址指针和块大小而定义的内存块中的字符不包含可跟踪的指针。

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>parameters

*ptr*\
第一个字符的地址，该字符不再包含可跟踪的指针。

size\
从不包含可跟踪指针的*ptr*开始的块大小。

### <a name="remarks"></a>备注

函数通知任何垃圾回收器范围内的地址 `[ ptr, ptr + size)` 不再包含可跟踪的指针。 （除非变为可访问，否则不能取消引用指向分配存储的任何指针。）

## <a name="declare_reachable"></a>declare_reachable

通知垃圾回收器：所指示的地址属于分配的存储并可到达。

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>parameters

*ptr*\
指向可访问、已分配且有效的存储区域的指针。

### <a name="remarks"></a>备注

如果*ptr*不为 null，则函数会通知任何垃圾回收器*ptr*现在可以访问，也就是说，它指向有效分配的存储。

## <a name="default_delete"></a>default_delete

删除用**new 运算符**分配的对象。 适用于[unique_ptr](unique-ptr-class.md)。

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>parameters

*ptr*\
指向要删除的对象的指针。

*其他*\
要删除的数组中的元素类型。

### <a name="remarks"></a>备注

类模板描述了一个删除器，该对象删除使用**new 运算符**分配的标量对象，适合与类模板 `unique_ptr`一起使用。 它还具有显式专用化 `default_delete<T[]>`。

## <a name="destroy_at"></a>destroy_at

```cpp
template <class T>
void destroy_at(
    T* location);
```

与 `location->~T()` 相同。

## <a name="destroy"></a>破坏

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

与相同：

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a>destroy_n

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

与相同：

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a>dynamic_pointer_cast

动态强制转换为[shared_ptr](shared-ptr-class.md)。

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>parameters

*T*\
由返回的共享指针控制的类型。

*其他*\
由自变量共享指针控制的类型。

*sp*\
自变量共享指针。

### <a name="remarks"></a>备注

如果 `dynamic_cast<T*>(sp.get())` 返回空指针，则模板函数将返回空的 `shared_ptr` 对象;否则，它将返回拥有*sp*拥有的资源的 `shared_ptr<T>` 对象。 表达式 `dynamic_cast<T*>(sp.get())` 必须有效。

### <a name="example"></a>示例

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a>get_deleter

从[shared_ptr](shared-ptr-class.md)获取删除器。

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>parameters

*删除器*\
删除器的类型。

*T*\
由共享指针控制的类型。

*sp*\
共享的指针。

### <a name="remarks"></a>备注

模板函数返回指向*删除器*类型的删除器的指针，该类型属于 `shared_ptr` 对象*sp*。 如果*sp*没有删除器，或者其删除器不是*删除器*类型，则该函数返回0。

### <a name="example"></a>示例

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>get_pointer_safety

返回任意垃圾回收器所采用的指针安全类型。

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>备注

函数返回任何自动垃圾回收器所采用的指针安全类型。

## <a name="get_temporary_buffer"></a>get_temporary_buffer

为不超过指定元素数量的元素序列分配临时存储。

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>parameters

*计数*\
所请求的、要为其分配内存的元素的最大数目。

### <a name="return-value"></a>返回值

一个 `pair`，其第一个组件是一个指向已分配内存的指针，其第二个组件提供缓冲区的大小，指示它可以存储的元素的最大数目。

### <a name="remarks"></a>备注

该函数发出内存请求，该请求可能不会成功。 如果没有分配缓冲区，则该函数将返回一个 pair，其第二个组件等于零，第一个组件等于空指针。

仅将此函数用于临时内存。

### <a name="example"></a>示例

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
        << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a>make_shared

创建并返回一个[shared_ptr](shared-ptr-class.md) ，该指向通过使用默认分配器从零个或多个参数构造的分配对象。 分配并构造指定类型的对象和`shared_ptr`来管理对象的共享所有权，并返回`shared_ptr`。

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>parameters

*args*\
零个或多个构造函数参数。 函数根据所提供的自变量来推断要调用的构造函数重载。

### <a name="remarks"></a>备注

使用`make_shared`作为创建对象的简单、更高效的方法，以及一个`shared_ptr`来同时管理对对象的共享访问。 在语义上，这两个语句是等效的：

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

但是，第一条语句进行了两个分配，如果在`shared_ptr`对象的分配成功后，`Example`的分配失败，则未命名的`Example`对象将被泄漏。 使用`make_shared`的语句更简单，因为只涉及到一个函数调用。 这样会更有效，因为库可能会对对象和智能指针进行一个分配。 此函数的速度更快，导致内存碎片更少，但在一次分配时不存在异常，而不是在另一种分配上。 通过使引用对象和更新智能指针中的引用计数的代码具有的更好的地址来提高性能。

如果不需要对象的共享访问权限，请考虑使用[make_unique](memory-functions.md#make_unique) 。 如果需要为对象指定自定义的分配器，请使用 [allocate_shared](memory-functions.md#allocate_shared)。 如果您的对象需要自定义删除器，则不能使用 `make_shared`，因为无法将删除器作为参数传递。

以下示例演示如何通过调用特定构造函数重载来创建指向类型的共享指针。

### <a name="example"></a>示例

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
    std::wstring title_;
    std::wstring artist_;

    Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
    Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers()
{
    // Okay, but less efficient to have separate allocations for
    // Song object and shared_ptr control block.
    auto song = new Song(L"Ode to Joy", L"Beethoven");
    std::shared_ptr<Song> sp0(song);

    // Use make_shared function when possible. Memory for control block
    // and Song object are allocated in the same call:
    auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
    auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

    // make_shared infers which constructor to use based on the arguments.
    auto sp3 = std::make_shared<Song>(L"Greensleeves");

    // The playlist vector makes copies of the shared_ptr pointers.
    std::vector<std::shared_ptr<Song>> playlist;
    playlist.push_back(sp0);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    playlist.push_back(sp3);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

此示例产生以下输出：

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>make_unique

创建 [unique_ptr](unique-ptr-class.md) 并将其返回到指定类型的对象，该对象通过指定的自变量进行构建。

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>parameters

*T*\
`unique_ptr` 将指向的对象的类型。

*Args*\
*Args*指定的构造函数参数的类型。

*args*\
要传递给类型*T*的对象的构造函数的参数。

*元素*\
类型为*T*的元素的数组。

size\
新数组中要为其分配空间的元素的数目。

### <a name="remarks"></a>备注

第一个重载用于单个对象。 为数组调用第二个重载。 第三个重载阻止您在类型参数中指定数组大小（make_unique\<T [N] >）;当前标准不支持此构造。 当使用 `make_unique` 将 `unique_ptr` 创建到数组时，必须分别初始化数组元素。 可能更好的选择是使用[std：： vector](vector-class.md)，而不是使用此重载。

由于谨慎实现 `make_unique` 以获得异常安全，因此建议您使用 `make_unique` 而不是直接调用 `unique_ptr` 构造函数。

### <a name="example"></a>示例

下面的示例说明如何使用 `make_unique`。 有关更多示例，请参阅[如何：创建和使用 unique_ptr 实例](../cpp/how-to-create-and-use-unique-ptr-instances.md)。

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

如果您收到与 `unique_ptr` 有关的错误 C2280，则几乎可以肯定是因为您尝试调用其副本构造函数（此函数是一个已删除的函数）。

## <a name="owner_less"></a>owner_less

允许对共享指针和弱指针进行基于所有权的混合比较。 如果在成员函数 `owner_before`的右参数之前对左侧参数进行排序，则返回**true** 。

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>parameters

*左*\
共享指针或弱指针。

*right*\
共享指针或弱指针。

### <a name="remarks"></a>备注

类模板将其所有成员运算符定义为返回 `left.owner_before(right)`。

## <a name="reinterpret_pointer_cast"></a>reinterpret_pointer_cast

使用强制转换通过现有共享指针创建新 `shared_ptr`。

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>parameters

*ptr*\
对 `shared_ptr<U>`的引用。

### <a name="remarks"></a>备注

如果*ptr*为空，则新 `shared_ptr` 也为空，否则它将与*ptr*共享所有权。 新的共享指针是对 `reinterpret_cast<Y*>(ptr.get())`进行计算的结果，其中 `Y` 是 `typename std::shared_ptr<T>::element_type`的。 如果 `reinterpret_cast<T*>((U*)nullptr)` 的格式不正确，则行为是不确定的。

采用左值引用的模板函数是 c + + 17 中的新增功能。 采用右值引用的模板函数是 c + + 20 中的新增功能。

## <a name="return_temporary_buffer"></a>return_temporary_buffer

对使用 `get_temporary_buffer` 模板函数分配的临时内存执行解除分配。

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>parameters

*缓冲区*\
指向要取消分配的内存的指针。

### <a name="remarks"></a>备注

仅将此函数用于临时内存。

### <a name="example"></a>示例

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
         << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

    int* tempBuffer = resultPair.first;

    // Deallocates memory allocated with get_temporary_buffer
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>static_pointer_cast

静态强制转换为[shared_ptr](shared-ptr-class.md)。

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>parameters

*T*\
由返回的共享指针控制的类型。

*其他*\
由自变量共享指针控制的类型。

*sp*\
自变量共享指针。

### <a name="remarks"></a>备注

如果*sp*为空 `shared_ptr` 对象，则模板函数将返回空的 `shared_ptr` 对象;否则，它将返回拥有*sp*拥有的资源的 `shared_ptr<T>` 对象。 表达式 `static_cast<T*>(sp.get())` 必须有效。

### <a name="example"></a>示例

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a>购

交换两个[shared_ptr](shared-ptr-class.md)、 [unique_ptr](unique-ptr-class.md)或[weak_ptr](weak-ptr-class.md)对象。

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>parameters

*T*\
由自变量指针控制的类型。

*删除器*\
唯一指针类型的删除器。

*左*\
左指针。

*right*\
右指针。

### <a name="remarks"></a>备注

模板函数调用 `left.swap(right)`。

### <a name="example"></a>示例

```cpp
// std__memory__swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="undeclare_no_pointers"></a>undeclare_no_pointers

通知垃圾回收器：通过基地址指针和块大小而定义的内存块中的字符现在可包含可跟踪的指针。

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>parameters

*ptr*\
指向以前使用[declare_no_pointers](#declare_no_pointers)标记的内存地址的指针。

size\
内存范围中的字节数。 此值必须等于 `declare_no_pointers` 调用中使用的数字。

### <a name="remarks"></a>备注

函数通知任何垃圾回收器 `[ptr, ptr + size)` 的地址范围现在可以包含可跟踪的指针。

## <a name="undeclare_reachable"></a>undeclare_reachable

撤消指定内存位置的可访问性声明。

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>parameters

*ptr*\
指向以前使用[declare_reachable](#declare_reachable)标记的内存地址的指针。

### <a name="remarks"></a>备注

如果*ptr*不为**nullptr**，则函数会通知任何垃圾回收器， *ptr*将无法再访问。 它将返回与*ptr*比较的安全派生的指针。

## <a name="uninitialized_copy"></a>uninitialized_copy

将指定源范围中的对象复制到未初始化的目标范围。

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
确定源范围中第一个元素的地址的输入迭代器。

*最后*\
确定源范围中最后一个元素的地址的输入迭代器。

*dest*\
确定目标范围中第一个元素的地址的前向迭代器。

### <a name="return-value"></a>返回值

用于寻址目标范围之外的第一个位置的前向迭代器，除非源范围为空。

### <a name="remarks"></a>备注

该算法可将内存分配与对象构造分离开。

该模板函数有效执行以下操作：

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

除非代码引发异常。 在这种情况下，所有构造的对象将销毁，并重新引发异常。

具有执行策略的重载是在 c + + 17 中新增的。

### <a name="example"></a>示例

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a>uninitialized_copy_n

创建来自输入迭代器的指定数量的元素的副本。 副本放置在向前迭代器中。

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
引用要复制的对象的输入迭代器。

*计数*\
指定复制对象的次数的带符号或无符号整数类型。

*dest*\
引用新副本所在位置的向前迭代器。

### <a name="return-value"></a>返回值

发现超出目标的第一个位置的向前迭代器。 如果源范围为空，则迭代器*首先*寻址。

### <a name="remarks"></a>备注

模板函数有效执行以下代码：

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

除非代码引发异常。 在这种情况下，所有构造的对象将销毁，并重新引发异常。

具有执行策略的重载是在 c + + 17 中新增的。

## <a name="uninitialized_default_construct"></a>uninitialized_default_construct

默认在指定范围内构造迭代器 "`value_type` 的对象。

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
用于寻址范围中要构造的第一个元素的迭代器。

*最后*\
一个迭代器，用于寻址要构造的范围中最后一个元素之后的一个元素。

### <a name="remarks"></a>备注

没有执行策略的版本实际上与相同：

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

如果引发异常，则将以未指定的顺序销毁以前构造的对象。

具有执行策略的版本具有相同的结果，但会根据指定的*策略*执行。

这些函数是 c + + 17 中的新增功能。

## <a name="uninitialized_default_construct_n"></a>uninitialized_default_construct_n

默认情况下，从指定位置开始构造迭代器 `value_type`的指定数目的对象。

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
一个迭代器，用于寻址要构造的目标范围中的第一个元素。

*计数*\
要构造的目标范围中的元素计数。

### <a name="return-value"></a>返回值

用于寻址目标范围之外的第一个位置的前向迭代器，除非源范围为空。

### <a name="remarks"></a>备注

没有执行策略的版本实际上与相同：

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

如果引发异常，则将以未指定的顺序销毁以前构造的对象。

具有执行策略的版本具有相同的结果，但会根据指定的*策略*执行。

这些函数是 c + + 17 中的新增功能。

## <a name="uninitialized_fill"></a>uninitialized_fill

将具有指定值的对象复制到未初始化的目标范围。

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
一个向前迭代器，用于寻址要初始化的目标范围中的第一个元素。

*最后*\
一个向前迭代器，用于寻址要初始化的目标范围中的最后一个元素。

*value*\
用于初始化目标范围的值。

### <a name="remarks"></a>备注

该算法可将内存分配与对象构造分离开。

该模板函数有效执行以下操作：

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

除非代码引发异常。 在这种情况下，所有构造的对象将销毁，并重新引发异常。

具有执行策略的重载是在 c + + 17 中新增的。

### <a name="example"></a>示例

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>uninitialized_fill_n

将指定值的对象复制到未初始化目标范围的指定数量的元素中。

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
一个向前迭代器，用于寻址要初始化的目标范围中的第一个元素。

*计数*\
要初始化的元素的数目。

*value*\
用于初始化目标范围的值。

### <a name="remarks"></a>备注

该算法可将内存分配与对象构造分离开。

该模板函数有效执行以下操作：

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

除非代码引发异常。 在这种情况下，所有构造的对象将销毁，并重新引发异常。

具有执行策略的重载是在 c + + 17 中新增的。

### <a name="example"></a>示例

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a>uninitialized_move

将源范围中的元素移动到未初始化的目标内存区域。

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
一种输入迭代器，用于寻址源范围中要移动的第一个元素。

*最后*\
一种输入迭代器，用于寻址源范围中要移动的最后一个元素之后的一个元素。

*dest*\
目标范围的开头。

### <a name="remarks"></a>备注

没有执行策略的版本实际上与相同：

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

如果引发异常，则可能会将源范围中的某些对象保留为有效但未指定的状态。 以前构造的对象将按未指定的顺序销毁。

具有执行策略的版本具有相同的结果，但会根据指定的*策略*执行。

这些函数是 c + + 17 中的新增功能。

## <a name="uninitialized_move_n"></a>uninitialized_move_n

将指定数量的元素从源范围移动到未初始化的目标内存区域。

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
一种输入迭代器，用于寻址源范围中要移动的第一个元素。

*计数*\
要移动的源范围中的元素计数。

*dest*\
目标范围的开头。

### <a name="remarks"></a>备注

没有执行策略的版本实际上与相同：

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

如果引发异常，则可能会将源范围中的某些对象保留为有效但未指定的状态。 以前构造的对象将按未指定的顺序销毁。

具有执行策略的版本具有相同的结果，但会根据指定的*策略*执行。

这些函数是 c + + 17 中的新增功能。

## <a name="uninitialized_value_construct"></a>uninitialized_value_construct

用指定范围内的值初始化构造迭代器的对象 `value_type`。

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
一个迭代器，用于寻址值构造范围内的第一个元素。

*最后*\
一个迭代器，用于寻址到值构造范围内最后一个元素之后的元素。

### <a name="remarks"></a>备注

没有执行策略的版本实际上与相同：

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

如果引发异常，则将以未指定的顺序销毁以前构造的对象。

具有执行策略的版本具有相同的结果，但会根据指定的*策略*执行。

如果内存分配失败，则会引发 `std::bad_alloc` 异常。

这些函数是 c + + 17 中的新增功能。

## <a name="uninitialized_value_construct_n"></a>uninitialized_value_construct_n

从指定位置开始，从值初始化中构造迭代器 `value_type` 的指定数目的对象。

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>parameters

*策略*\
要使用的执行策略。

*第一个*\
一个迭代器，用于寻址要构造的目标范围中的第一个元素。

*计数*\
要构造的目标范围中的元素计数。

### <a name="remarks"></a>备注

没有执行策略的版本实际上与相同：

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

如果引发异常，则将以未指定的顺序销毁以前构造的对象。

具有执行策略的版本具有相同的结果，但会根据指定的*策略*执行。

如果内存分配失败，则会引发 `std::bad_alloc` 异常。

这些函数是 c + + 17 中的新增功能。

## <a name="uses_allocator_v"></a>uses_allocator_v

用于访问 `uses_allocator` 模板的值的帮助器变量模板。

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>另请参阅

[\<memory>](memory.md)
