---
title: '&lt;exception&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: aba17b7bf052b6974bf849f60ff895b8e84a1092
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427133"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;exception&gt; typedefs

## <a name="exception_ptr"></a>  exception_ptr

该类型描述指向异常的指针。

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>备注

用于实现 `exception_ptr` 类型的未指定的内部类。

使用 `exception_ptr` 对象可引用当前异常或用户指定异常的实例。 在 Microsoft 实现中，异常由 [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) 结构表示。 每个 `exception_ptr` 对象包含一个异常引用字段，该字段指向表示异常的 `EXCEPTION_RECORD` 结构的副本。

当你声明 `exception_ptr` 变量时，该变量不与任何异常相关联。 也就是说，其异常引用字段为 NULL。 此类 `exception_ptr` 对象称为 *null exception_ptr*。

使用 `current_exception` 或 `make_exception_ptr` 函数可将异常指派给 `exception_ptr` 对象。 将异常指派给 `exception_ptr` 变量时，该变量的异常引用字段将指向该异常的副本。 如果没有足够的内存来复制异常，异常引用字段将指向 [std::bad_alloc](../standard-library/bad-alloc-class.md) 异常的副本。 如果 `current_exception` 或 `make_exception_ptr` 函数因任何其他原因不能复制异常，该函数将调用 `terminate` CRT 函数以退出当前进程。

尽管名称像是一个指针，但 `exception_ptr` 对象本身不属于指针。 它不遵循指针语义，不能与指针成员访问 ( `->`) 或间接寻址 (*) 运算符一起使用。 `exception_ptr` 对象没有公共数据成员或成员函数。

**比较：**

可以使用相等 ( `==`) 和不相等 ( `!=`) 运算符比较两个 `exception_ptr` 对象。 这两个运算符不比较表示异常的 `EXCEPTION_RECORD` 结构的二进制值（位模式）， 而是比较 `exception_ptr` 对象的异常引用字段中的地址。 因此，null `exception_ptr` 和 NULL 值的比较结果为相等。

## <a name="terminate_handler"></a>terminate_handler

此类型描述适合用作 `terminate_handler` 的函数指针。

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>备注

此类型描述适合用作终止处理程序的函数指针。

### <a name="example"></a>示例

有关 [ 的使用示例，请参阅 ](../standard-library/exception-functions.md#set_terminate)set_terminate`terminate_handler`。

## <a name="unexpected_handler"></a>unexpected_handler

该类型描述适合用作 `unexpected_handler` 的函数指针。

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>示例

有关 [ 的使用示例，请参阅 ](../standard-library/exception-functions.md#set_unexpected)set_unexpected`unexpected_handler`。
