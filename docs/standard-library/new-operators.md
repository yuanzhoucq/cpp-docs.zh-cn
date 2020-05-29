---
title: '&lt;新的&gt; 运算符和枚举'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: a3fd5b825fe1eaf3a07d9d001f03b9d0c64ffa31
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425369"
---
# <a name="ltnewgt-operators-and-enums"></a>&lt;新的&gt; 运算符和枚举

## <a name="op_align_val_t"></a>枚举 align_val_t

```cpp
enum class align_val_t : size_t {};
```

## <a name="op_delete"></a>运算符删除

由 delete 表达式调用的函数，用于取消分配各个对象的存储。

```cpp
void operator delete(void* ptr) throw();
void operator delete(void *, void*) throw();
void operator delete(void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>parameters

*ptr*\
其值由删除呈现为无效的指针。

### <a name="remarks"></a>备注

第一个函数由 delete 表达式调用以呈现*ptr*的值无效。 该程序可以通过替换 C++ 标准库定义的默认版本的函数签名定义函数。 所需的行为是接受值为 null 或由对[运算符 new](../standard-library/new-operators.md#op_new)（**size_t**）之前调用返回的*ptr*值。

*Ptr*的 null 值的默认行为是不执行任何操作。 *Ptr*的任何其他值必须是前面所述的调用之前返回的值。 此类非空*值的默认行为是回收*之前调用分配的存储。 在哪些条件下指定了部分或全部此类回收的存储由对 `operator new`（**size_t**）或 `calloc`（ **size_t**）、`malloc`（ **size_t**）或 `realloc`（ **void** <strong>\*</strong>， **size_t**）的后续调用分配。

第二个函数由对应于 **new**( **std::size_t**) 形式的新表达式的 placement delete 表达式调用。 它不执行任何操作。

第三个函数由对应于 **new**( **std::size_t**, **conststd::nothrow_t&** ) 形式的新表达式的 placement delete 表达式调用。 该程序可以通过替换 C++ 标准库定义的默认版本的函数签名定义函数。 所需行为接受 `ptr` 的值，该值为 NULL 或由对 `operator new`(**size_t**) 的早期调用返回。 默认行为是评估**delete**（`ptr`）。

### <a name="example"></a>示例

有关使用**运算符 delete**的示例，请参阅[运算符 new](../standard-library/new-operators.md#op_new) 。

## <a name="op_delete_arr"></a>operator delete []

由 delete 表达式调用来解除对象数组的存储空间分配的函数。

```cpp
void operator delete[](void* ptr) throw();
void operator delete[](void *, void*) throw();
void operator delete[](void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>parameters

*ptr*\
其值由删除呈现为无效的指针。

### <a name="remarks"></a>备注

第一个函数由 `delete[]` 表达式调用，用于呈现*ptr*的值无效。 该函数为可替换，因为该程序可以通过替换 C++ 标准库定义的默认版本的函数签名定义函数。 所需的行为是接受值为 null 或由对[运算符 new&#91;](../standard-library/new-operators.md#op_new_arr)（**size_t**）之前调用返回的*ptr*值。 *Ptr*的 null 值的默认行为是不执行任何操作。 *Ptr*的任何其他值必须是前面所述的调用之前返回的值。 此类非 null*值的默认行为是回收*由之前的调用分配的存储。 在哪些条件下指定了部分或全部此类回收的存储由对[operator new](../standard-library/new-operators.md#op_new)（**size_t**）或 `calloc`（**size_t**）、`malloc`（**size_t**）或 `realloc`（ **void** <strong>\*</strong>， **size_t**）的后续调用分配。

第二个函数由与 `new[]`（**std：： size_t**）形式的 `new[]` 表达式对应的位置 `delete[]` 表达式调用。 它不执行任何操作。

第三个函数由对应于 `new[]`( `new[]`std::size_t **,** const std::nothrow_t& **) 形式的**  表达式的 placement delete 表达式调用。 该程序可以通过替换 C++ 标准库定义的默认版本的函数签名定义函数。 所需的行为是接受值为 null 或由对*运算符的先前*调用所返回的值 `new[]`（**size_t**）。 默认行为是评估 `delete[]`( `ptr`)。

### <a name="example"></a>示例

有关 [ 的使用示例，请参阅](../standard-library/new-operators.md#op_new_arr)运算符 new&#91;&#93;`operator delete[]`。

## <a name="op_new"></a>运算符 new

由 new 表达式调用来为单个对象分配存储空间的函数。

```cpp
void* operator new(std::size_t count) throw(bad_alloc);
void* operator new(std::size_t count, const std::nothrow_t&) throw();
void* operator new(std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>parameters

*计数*\
要分配的存储的字节数。

*ptr*\
要返回的指针。

### <a name="return-value"></a>返回值

指向新分配内存的最小字节地址的指针。 或*ptr*。

### <a name="remarks"></a>备注

第一个函数由 new 表达式调用，以便分配 `count` 个字节的存储，适当对齐该存储以表示该大小的任何对象。 该程序可以通过替换 C++ 标准库定义的默认版本的函数签名定义 alternate 函数，因此该程序为可替换。

仅在按照请求分配存储时，所需的行为才为返回非空指针。 每个此类分配都会向不与任何其他已分配的存储连接的存储生成指针。 未指定连续调用分配的存储的顺序和连续性。 未指定存储的初始值。 返回的指针指向已分配的存储的开始（最小字节地址）。 如果计数为零，则返回的值不与该函数返回的任何其他值相等。

默认行为是执行一个循环。 在此循环中，该函数会首先尝试分配请求的存储。 未指定该尝试是否涉及调用 `malloc`( **size_t**)。 如果尝试成功，则该函数将返回已分配存储的指针。 否则，该函数将调用指定的[新处理程序](../standard-library/new-typedefs.md#new_handler)。 返回被调用的函数时，将重复该循环。 尝试分配请求的存储成功时或未返回被调用的函数时，循环将终止。

新处理程序所需的行为是执行以下操作之一：

- 使更多存储可用于分配，然后返回。

- 调用**abort**或**exit**（`int`）。

- 引发一个 **bad_alloc** 类型的对象。

[新处理程序](../standard-library/new-typedefs.md#new_handler)的默认行为是引发一个 `bad_alloc` 类型的对象。 空指针指定新的默认处理程序。

`operator new`（**size_t**）连续调用分配的存储的顺序和邻接未指定，这与存储在该处的初始值相同。

第一个函数由 placement new 表达式调用，以便分配 `count` 个字节的存储，适当对齐该存储以表示该大小的任何对象。 该程序可以通过替换 C++ 标准库定义的默认版本的函数签名定义 alternate 函数，因此该程序为可替换。

如果该函数成功，则默认行为是返回 `operator new`（`count`）。 否则，它返回空指针。

第三个函数由 **new** ( **args**) T 形式的 placement *new* 表达式调用。此处，*args* 包含单个对象指针。 这可用于构造已知地址的对象。 该函数返回 *ptr*。

若要释放由**运算符 new**分配的存储，请调用[运算符 delete](../standard-library/new-operators.md#op_delete)。

有关新的引发或非引发行为的信息，请参阅[new 和 Delete 运算符](../cpp/new-and-delete-operators.md)。

### <a name="example"></a>示例

```cpp
// new_op_new.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;

class MyClass
{
public:
   MyClass( )
   {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass( )
   {
      imember = 0; cout << "Destructing MyClass." << this << endl;
   };
   int imember;
};

int main( )
{
   // The first form of new delete
   MyClass* fPtr = new MyClass;
   delete fPtr;

   // The second form of new delete
   MyClass* fPtr2 = new( nothrow ) MyClass;
   delete fPtr2;

   // The third form of new delete
   char x[sizeof( MyClass )];
   MyClass* fPtr3 = new( &x[0] ) MyClass;
   fPtr3 -> ~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;
}
```

## <a name="op_new_arr"></a>new 运算符 []

由 new 表达式调用来为对象数组分配存储空间的分配函数。

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);
void* operator new[](std::size_t count, const std::nothrow_t&) throw();
void* operator new[](std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>parameters

*计数*\
要为数组对象分配的存储的字节数。

*ptr*\
要返回的指针。

### <a name="return-value"></a>返回值

指向新分配内存的最小字节地址的指针。 或*ptr*。

### <a name="remarks"></a>备注

第一个函数由 `new[]` 表达式调用，以便分配 `count` 个字节的存储，适当对齐该存储以表示该大小或更小的任何数组对象。 该程序可以通过替换 C++ 标准库定义的默认版本的函数签名定义函数。 所需的行为与[运算符 new](../standard-library/new-operators.md#op_new)（**size_t**）相同。 默认行为是返回 `operator new`( `count`)。

第二个函数由 placement `new[]` 表达式调用，以便分配 `count` 个字节的存储，适当对齐该存储以表示该大小的任何数组对象。 该程序可以通过替换 C++ 标准库定义的默认版本的函数签名定义函数。 如果该函数成功，则默认行为是返回**operatornew**（`count`）。 否则，它返回空指针。

第三个函数由 `new[]`new **(** args *)* T **[** N **] 形式的 placement**  函数调用。 此处，*args* 包含单个对象指针。 该函数返回 `ptr`。

若要释放 `operator new[]` 分配的存储，请调用[运算符 delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)。

有关 new 的引发或非引发行为的信息，请参阅 [new 和 delete 运算符](../cpp/new-and-delete-operators.md)。

### <a name="example"></a>示例

```cpp
// new_op_alloc.cpp
// compile with: /EHsc
#include <new>
#include <iostream>

using namespace std;

class MyClass {
public:
   MyClass() {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass() {
      imember = 0; cout << "Destructing MyClass." << this << endl;
      };
   int imember;
};

int main() {
   // The first form of new delete
   MyClass* fPtr = new MyClass[2];
   delete[ ] fPtr;

   // The second form of new delete
   char x[2 * sizeof( MyClass ) + sizeof(int)];

   MyClass* fPtr2 = new( &x[0] ) MyClass[2];
   fPtr2[1].~MyClass();
   fPtr2[0].~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;

   // The third form of new delete
   MyClass* fPtr3 = new( nothrow ) MyClass[2];
   delete[ ] fPtr3;
}
```
