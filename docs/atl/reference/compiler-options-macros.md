---
title: 编译器选项宏
ms.date: 08/19/2019
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
ms.openlocfilehash: 702324c3300ff23bb60113529a681e3b8fa99354
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331623"
---
# <a name="compiler-options-macros"></a>编译器选项宏

这些宏控制特定的编译器功能。

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|启用从早期版本的 ATL 转换的项目中的错误的符号。|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|定义一个或多个对象是否使用公寓线程。|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|使某些`CString`构造函数成为显式，防止任何无意转换。|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|定义此宏以便使用C++标准兼容的语法，当使用非标准语法初始化指向成员函数的指针时，该语法会生成 C4867 编译器错误。|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|定义一个或多个对象是否使用自由线程或中性线程。|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|指示项目将具有标记为"两者"、"自由"或"中性"的对象的符号。 应改为使用宏[_ATL_FREE_THREADED。](#_atl_free_threaded)|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|防止默认使用命名空间作为 ATL 的符号。|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|阻止与 COM 相关的代码与项目一起编译的符号。|
|[ATL_NO_VTABLE](#atl_no_vtable)|阻止在类的构造函数和析构函数中初始化 vtable 指针的符号。|
|[ATL_NOINLINE](#atl_noinline)|指示函数的符号不应内联。|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|定义是否所有对象都使用单个线程模型。|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

启用从早期版本的 ATL 转换的项目中的错误的符号。

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>备注

在 Visual C++ .NET 2002 之前，ATL 禁用了许多警告并将其禁用，以便它们永远不会出现在用户代码中。 具体来说：

- C4127 条件表达式是常量表达式

- C4786"标识符"：标识符被截断为调试信息中的"数字"字符

- 使用 C4201 非标准扩展：无名结构/联合

- C4103"文件名"：使用#pragma包更改对齐方式

- C4291"声明"：未找到匹配的运算符删除;如果初始化引发异常，则不会释放内存

- C4268"标识符"："使用编译器生成的默认构造函数初始化的"const"静态/全局数据用零填充对象

- C4702 无法访问的代码

在从早期版本转换的项目中，库标头仍禁用这些警告。

通过在包含库标头之前将以下行添加到*pch.h（Visual* Studio 2017 和更早版本中的*stdafx.h）* 文件中，可以更改此行为。

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

如果添加了`#define`此选项，ATL 标头将小心保留这些警告的状态，以便它们不会全局禁用（或者如果用户显式禁用单个警告，而不是启用它们）。

默认情况下，新项目在`#define` *pch.h（Visual* Studio 2017 和更早版本中的*stdafx.h）* 中设置了此集。

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

定义一个或多个对象是否使用公寓线程。

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>备注

指定公寓线程。 有关其他线程选项，请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)，以及[ATL 简单对象向导选项](../../atl/reference/options-atl-simple-object-wizard.md)，了解可用于 ATL 对象的线程模型的说明。

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

使某些`CString`构造函数成为显式，防止任何无意转换。

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>备注

定义此构造函数时，使用显式关键字编译采用单个参数的所有 CString 构造函数，从而阻止输入参数的隐式转换。 例如，这意味着在定义_UNICODE时，如果尝试使用 char* 字符串作为 CString 构造函数参数，则会导致编译器错误。 在需要防止窄字符串类型和宽字符串类型之间的隐式转换的情况下使用此宏。

通过对所有构造函数字符串参数使用_T宏，可以定义_ATL_CSTRING_EXPLICIT_CONSTRUCTORS并避免编译错误，而不管是否定义了_UNICODE。

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

定义此宏以强制使用 ANSI C++标准兼容的语法来指向成员函数的指针。 使用此宏将导致使用非标准语法初始化指向成员函数的指针时生成 C4867 编译器错误。

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>备注

ATL 和 MFC 库已更改，以匹配 Microsoft C++编译器改进的标准C++合规性。 根据 ANSI C++标准，指向类成员函数的指针的语法应为`&CMyClass::MyFunc`。

如果未定义[_ATL_ENABLE_PTM_WARNING（](#_atl_enable_ptm_warning)默认情况），ATL/MFC 会禁用宏映射中的 C4867 错误（尤其是消息映射），以便在早期版本中创建的代码可以继续像以前那样生成。 如果定义 **_ATL_ENABLE_PTM_WARNING，** 则代码应C++标准兼容。

但是，非标准窗体已被弃用。 您需要将现有代码移动到C++标准兼容的语法。 例如，以下代码：

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

应当更改为：

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

对于地图宏，添加放大器和"&"字符。 不应在代码中再次添加该字符。

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

定义一个或多个对象是否使用自由线程或中性线程。

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>备注

指定自由线程。 自由线程等效于多线程单元模型。 有关其他线程选项，请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)，以及[ATL 简单对象向导选项](../../atl/reference/options-atl-simple-object-wizard.md)，了解可用于 ATL 对象的线程模型的说明。

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

指示项目将具有标记为"两者"、"自由"或"中性"的对象的符号。

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>备注

如果定义了此符号，ATL 将提取正确同步对全局数据的访问的代码。 新代码应使用等效的宏[_ATL_FREE_THREADED。](#_atl_free_threaded)

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

防止默认使用命名空间作为 ATL 的符号。

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>备注

如果未定义此符号，则包括 atlbase.h 默认**使用命名空间 ATL**执行，这可能导致命名冲突。 为了防止这种情况，请定义此符号。

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

阻止与 COM 相关的代码与项目一起编译的符号。

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a>ATL_NO_VTABLE

阻止在类的构造函数和析构函数中初始化 vtable 指针的符号。

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>备注

如果阻止在类的构造函数和析构函数中初始化 vtable 指针，则链接器可以消除 vtable 及其指向的所有函数。 扩展到 **__declspec（可更新的）**。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a>ATL_NOINLINE

指示函数的符号不应内联。

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>参数

*我的功能*<br/>
不应内联的函数。

### <a name="remarks"></a>备注

如果要确保函数不会由编译器内联，即使必须将其声明为内联，以便将其放置在标头文件中，也可以使用此符号。 扩展到 **__declspec（名词）**。

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

定义所有对象是否使用单个线程模型

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>备注

指定对象始终在主 COM 线程中运行。 有关其他线程选项，请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)，以及[ATL 简单对象向导选项](../../atl/reference/options-atl-simple-object-wizard.md)，了解可用于 ATL 对象的线程模型的说明。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
