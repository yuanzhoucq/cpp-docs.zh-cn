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
ms.openlocfilehash: d8c9538c9f3d889360c0527ba538e9e091df0755
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229956"
---
# <a name="compiler-options-macros"></a>编译器选项宏

这些宏控制特定的编译器功能。

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|一个符号，用于在从早期版本的 ATL 转换的项目中启用错误。|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|定义一个或多个对象是否使用单元线程处理。|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|使某些 `CString` 构造函数明确，防止任何意外转换。|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|定义此宏以便使用 c + + 标准兼容语法，这会在使用非标准语法初始化指向成员函数的指针时生成 C4867 编译器错误。|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|定义一个或多个对象是否使用自由或非特定线程。|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|一个符号，指示项目将具有标记为 "免费" 或 "非特定" 的对象。 应改为使用宏[_ATL_FREE_THREADED](#_atl_free_threaded) 。|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|阻止默认使用命名空间作为 ATL 的符号。|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|一种阻止与 COM 相关的代码与你的项目一起编译的符号。|
|[ATL_NO_VTABLE](#atl_no_vtable)|一个符号，该符号阻止在类的构造函数和析构函数中初始化 vtable 指针。|
|[ATL_NOINLINE](#atl_noinline)|指示函数不应内联的符号。|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|定义所有对象是否均使用单个线程模型。|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

一个符号，用于在从早期版本的 ATL 转换的项目中启用错误。

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>备注

在 Visual C++ .NET 2002 之前，ATL 禁用了许多警告，并将其禁用，以使它们永远不会显示在用户代码中。 具体而言：

- C4127 条件表达式是常量

- C4786 "identifier"：标识符被截断为调试信息中的 "number" 个字符

- 使用的 C4201 非标准扩展：无号结构/联合

- C4103 "filename"：用于更改对齐方式 #pragma pack

- C4291 "声明"：未找到匹配的运算符 delete;如果初始化引发异常，则不会释放内存

- C4268 "identifier"：用编译器生成的默认构造函数初始化的 "const" 静态/全局数据用零填充对象

- C4702 无法访问的代码

在从以前版本转换而来的项目中，库标头仍禁用这些警告。

通过在包含库标头之前，将以下行添加到*pch* （Visual Studio 2017 及更早版本）文件中的*stdafx.h* ，可以更改此行为。

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

如果 `#define` 添加了此操作，ATL 标头将小心保留这些警告的状态，以使它们不会被全局禁用（或者，如果用户显式禁用各个警告，而不是启用它们）。

`#define`默认情况下，新项目在*Pch* （Visual Studio 2017 及更早版本）*中具有*此设置。

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

定义一个或多个对象是否使用单元线程处理。

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>备注

指定单元线程。 有关适用于 ATL 对象的线程模型的说明，请参阅为其他线程处理选项[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)和[选项，Atl 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)。

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

使某些 `CString` 构造函数明确，防止任何意外转换。

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>备注

如果定义了此构造函数，则采用单个参数的所有 CString 构造函数都将使用 explicit 关键字进行编译，这会阻止输入参数的隐式转换。 这意味着，例如，在定义 _UNICODE 时，如果尝试使用 char * 字符串作为 CString 构造函数参数，则会产生编译器错误。 如果需要防止在窄到宽字符串类型之间进行隐式转换，请使用此宏。

通过对所有构造函数字符串参数使用 _T 宏，无论是否定义 _UNICODE，都可以定义 _ATL_CSTRING_EXPLICIT_CONSTRUCTORS 并避免编译错误。

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

定义此宏是为了强制将 ANSI c + + 标准兼容语法用于指向成员函数的指针。 如果使用非标准语法初始化指向成员函数的指针，则使用此宏将导致生成 C4867 编译器错误。

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>备注

ATL 和 MFC 库已更改，与 Microsoft c + + 编译器改进的标准 c + + 相容性相匹配。 根据 ANSI c + + 标准，指向类成员函数的指针的语法应该是 `&CMyClass::MyFunc` 。

如果未定义[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) （默认情况），ATL/MFC 将禁用宏映射中的 C4867 错误（特别是消息映射），以便在早期版本中创建的代码可以继续像以前一样构建。 如果定义 **_ATL_ENABLE_PTM_WARNING**，则代码应符合 c + + 标准。

但是，非标准窗体已弃用。 需要将现有代码移到 c + + 标准兼容语法。 例如，以下代码：

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

应当更改为：

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

对于映射宏，请添加 "&" 字符。 不应在代码中再次添加字符。

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

定义一个或多个对象是否使用自由或非特定线程。

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>备注

指定自由线程处理。 自由线程处理等效于多线程单元模型。 有关适用于 ATL 对象的线程模型的说明，请参阅为其他线程处理选项[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)和[选项，Atl 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)。

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

一个符号，指示项目将具有标记为 "免费" 或 "非特定" 的对象。

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>备注

如果定义了此符号，则 ATL 将提取可正确同步对全局数据的访问的代码。 新代码应改为使用等效的宏[_ATL_FREE_THREADED](#_atl_free_threaded) 。

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

阻止默认使用命名空间作为 ATL 的符号。

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>备注

如果未定义此符号，则默认情况下，包括 atlbase.h 将**使用命名空间 ATL**执行，这可能会导致命名冲突。 若要防止出现这种情况，请定义此符号。

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

一种阻止与 COM 相关的代码与你的项目一起编译的符号。

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a>ATL_NO_VTABLE

一个符号，该符号阻止在类的构造函数和析构函数中初始化 vtable 指针。

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>备注

如果无法在类的构造函数和析构函数中初始化 vtable 指针，则链接器可以消除 vtable 以及它指向的所有函数。 将扩展到 **`__declspec(novtable)`** 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a>ATL_NOINLINE

指示函数不应内联的符号。

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>参数

*myfunction*<br/>
不应内联的函数。

### <a name="remarks"></a>备注

如果要确保编译器不会内联函数，请使用此符号，即使它必须声明为内联，以便可以将其放置在标头文件中。 将扩展到 **`__declspec(noinline)`** 。

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

定义所有对象是否使用单线程模型

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>备注

指定对象始终在主 COM 线程中运行。 有关适用于 ATL 对象的线程模型的说明，请参阅为其他线程处理选项[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)和[选项，Atl 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
