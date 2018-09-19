---
title: 编译器选项宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63fa47f4237d27cb8e0d5629e2041244ab360132
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075093"
---
# <a name="compiler-options-macros"></a>编译器选项宏

这些宏控制特定的编译器功能。

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|这样项目中的错误的符号转换从早期版本的 atl。|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|如果一个或多个对象使用单元线程处理，定义。|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|可确保`CString`显式，防止任何意外的转换构造函数。|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|定义此宏，以便使用 c + + 标准兼容的语法，它在非标准语法用于初始化的指针到成员函数时生成 C4867 编译器错误。|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|如果一个或多个对象使用免费的还是中立线程，定义。|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|指示项目符号会标记为两者，免费或非特定于的对象。 该宏[_ATL_FREE_THREADED](#_atl_free_threaded)应改为使用。|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|一个符号，这将阻止默认使用命名空间作为 atl。|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|这样可防止 COM 相关的代码与你的项目正在编译的符号。|
|[ATL_NO_VTABLE](#atl_no_vtable)|正在初始化类的构造函数和析构函数中阻止 vtable 指针符号。|
|[ATL_NOINLINE](#atl_noinline)|符号，指示函数不应为内联。|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|如果所有对象都使用单线程模型中，定义。|

##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS

这样项目中的错误的符号转换从早期版本的 atl。

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>备注

Visual c + +.NET 2002年之前 ATL 禁用的警告的很多并保留其禁用，以便它们永远不会显示在用户代码中。 尤其是在下列情况下：

- C4127 条件表达式是常量

- C4786 identifier： 标识符被截断为 number 个字符中的调试信息

- 使用 C4201 了非标准扩展： 无名称结构/联合

- C4103 filename: #pragma 包用于更改对齐方式

- C4291 declaration： 没有匹配的删除运算符; 如果找到如果初始化引发异常，不会释放内存

- C4268 identifier： 用编译器生成默认构造函数初始化 const 静态/全局数据填充了零对象

- C4702 无法访问的代码

在从以前版本转换项目中，这些警告将仍处于禁用状态由库标头。

通过将以下行添加到 stdafx.h 文件中包括库标头之前，可以更改此行为。

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

如果此`#define`添加，ATL 标头非常小心地保留这些警告的状态，以便它们不被全局禁用 （或用户显式禁用个别警告，无法启用它们）。

新项目都具有这`#define`在 stdafx.h 中默认情况下设置。

##  <a name="_atl_apartment_threaded"></a>  _ATL_APARTMENT_THREADED

如果一个或多个对象使用单元线程处理，定义。

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>备注

指定单元线程处理。 请参阅[指定项目的线程处理模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)适用于其他线程处理选项，并[选项，ATL 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)有关线程处理的说明可用于 ATL 对象进行建模。

##  <a name="_atl_cstring_explicit_constructors"></a>  _ATL_CSTRING_EXPLICIT_CONSTRUCTORS

可确保`CString`显式，防止任何意外的转换构造函数。

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>备注

这定义时，所有 CString 构造函数采用单个参数的都编译的显式关键字，这样可以防止隐式转换的输入参数。 这意味着，如果定义了 _UNICODE，如果尝试使用 char * 字符串作为 CString 构造函数参数，将导致编译器错误。 在需要阻止窄和宽字符串类型之间的隐式转换的情况下使用此宏。

通过对所有构造函数字符串自变量使用 _T 宏，可以定义 _ATL_CSTRING_EXPLICIT_CONSTRUCTORS 和避免编译错误，无论是否定义了 _UNICODE。

##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING

定义此宏，以便强制对成员函数的指针的 ANSI c + + 的符合标准的语法的使用。 使用此宏将导致 C4867 编译器错误生成时使用非标准语法来初始化指向成员函数的指针。

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>备注

已更改的 ATL 和 MFC 库以匹配 Visual c + + 编译器改进标准 c + + 合规性。 根据 ANSI c + + 标准中，指向类成员函数的指针的语法应为`&CMyClass::MyFunc`。

当[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)未定义 （默认情况下），以便在早期版本中创建的代码可以继续像以前那样生成 ATL/MFC 禁用 C4867 错误 （值得注意的是消息映射） 的宏映射中。 如果定义了 **_ATL_ENABLE_PTM_WARNING**，你的代码应为 c + + 标准合规。

但是，非标准窗体已被弃用，因此您需要将现有代码移到 c + + 标准的符合语法。 例如，以下内容：

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

应更改为：

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

请注意，添加 & 字符映射宏，你应将其添加再次在代码中。

##  <a name="_atl_free_threaded"></a>  _ATL_FREE_THREADED

如果一个或多个对象使用免费的还是中立线程，定义。

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>备注

指定自由线程处理。 自由线程处理相当于多线程单元模型。 请参阅[指定项目的线程处理模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)适用于其他线程处理选项，并[选项，ATL 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)有关线程处理的说明可用于 ATL 对象进行建模。

##  <a name="_atl_multi_threaded"></a>  _ATL_MULTI_THREADED

指示项目符号会标记为两者，免费或非特定于的对象。

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>备注

如果定义此符号，则会将正确同步到的全局数据的访问的代码中拉取 ATL。 新代码应使用等效的宏[_ATL_FREE_THREADED](#_atl_free_threaded)相反。

##  <a name="_atl_no_automatic_namespace"></a>  _ATL_NO_AUTOMATIC_NAMESPACE

一个符号，这将阻止默认使用命名空间作为 atl。

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>备注

如果未定义此符号，则将执行包括 atlbase.h**使用 ATL 的命名空间**默认情况下，这可能会导致命名冲突。 若要防止此情况，定义此符号。

##  <a name="_atl_no_com_support"></a>  _ATL_NO_COM_SUPPORT

这样可防止 COM 相关的代码与你的项目正在编译的符号。

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE

正在初始化类的构造函数和析构函数中阻止 vtable 指针符号。

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>备注

如果 vtable 指针阻止正在初始化类的构造函数和析构函数中，链接器可以消除 vtable 和所有它所指向的函数。 将扩展到 **__declspec （novtable)**。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>  ATL_NOINLINE

符号，指示函数不应为内联。

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>参数

*myfunction*<br/>
不应为内联函数。

### <a name="remarks"></a>备注

如果你想要确保函数不会由编译器内联即使必须声明为内联，以便它可以放置在头文件中，请使用此符号。 将扩展到 **__declspec （noinline)**。

##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED

如果所有对象都使用单线程模型中，定义

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>备注

指定对象始终在主 COM 线程中运行。 请参阅[指定项目的线程处理模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)适用于其他线程处理选项，并[选项，ATL 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)有关线程处理的说明可用于 ATL 对象进行建模。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
