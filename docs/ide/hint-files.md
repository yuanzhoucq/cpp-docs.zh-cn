---
title: 提示文件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- cpp.hint
- vc.hint.file
dev_langs:
- C++
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98734522410b867d735d0af25f440d5b45874563
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393277"
---
# <a name="hint-files"></a>提示文件

提示文件可帮助 Visual Studio 集成开发环境 (IDE) 解释 Visual C++ 标识符，例如函数和宏的名称。 打开 Visual C++ 项目时，IDE 的分析系统会分析项目中每个源文件中的代码，并收集每个标识符的相关信息。 然后，IDE 使用该信息来支持诸如“类视图”浏览器和“导航栏”等功能。

Visual C++ 2010 中引入的分析系统可识别 C/C++ 语法，但可能会错误解释包含宏的语句。 如果宏导致写入源代码时语法不正确，则可能会错误解释该语句。 编译源代码且预处理器用其定义替换[宏标识符](../preprocessor/hash-define-directive-c-cpp.md)时，语句的语法可能是正确的。 分析系统无需生成项目即可运行，因为它使用提示文件来解释宏。 因此，“类视图”等浏览功能立即可用。

提示文件包含用户自定义的提示，其语法与 C/C++ 宏定义相同。 Visual C++ 包含一个内置提示文件，足以满足大多数项目的需求，但可自行创建提示文件来改进 Visual Studio 处理标识符的方式。

> [!IMPORTANT]
> 如果修改或添加提示文件，则必须删除解决方案中的 .sdf 文件和/或 VC.db 文件才能使更改生效。

## <a name="scenario"></a>方案

假设以下代码位于使用“类视图”进行检查的源文件中。 `STDMETHOD` 宏声明一个 `myMethod` 方法，该方法接受一个参数并返回指向 HRESULT 的指针。

```cpp
// Source code file.
STDMETHOD(myMethod)(int parameter1);
```

以下宏定义位于单独的头文件中。

```cpp
// Header file.
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)
#define STDMETHODCALLTYPE __stdcall
#define HRESULT void*
```

分析系统无法解释源代码，因为名为 `STDMETHOD` 的函数似乎已声明，且该声明在语法上是不正确的，因为它有两个参数列表。 分析系统不会打开头文件来发现 `STDMETHOD`、`STDMETHODCALLTYPE` 和 `HRESULT` 宏的定义。 由于分析系统无法解释 `STDMETHOD` 宏，因此它会忽略整个语句，然后继续分析。

分析系统不使用头文件，因为项目可能依赖于一个或多个重要的头文件。 如果任何头文件发生更改，分析系统可能需要重新检查项目中的所有头文件，这会降低 IDE 的性能。 相反，分析系统使用指定如何处理 `STDMETHOD`、`STDMETHODCALLTYPE` 和 `HRESULT` 宏的提示。

如何知道需要提示？ 如果需要提示，应创建哪种类型的提示？ 需要提示的标志是“类视图”中标识符的视图与“编辑器”中的视图不一致。 例如，“类视图”可能不显示已知存在的类成员，或该成员的名称不正确。 若要详细了解用于解决常见问题的提示类型，请参阅本主题后面的“哪些宏需要提示？”部分。

## <a name="architecture"></a>体系结构

提示文件位于物理目录，而不是解决方案资源管理器中描述的逻辑目录。 无需将提示文件添加到项目中即可使提示文件生效。 分析系统仅在分析源文件时使用提示文件。

每个提示文件均命名为 cpp.hint。 因此，提示文件可包含在多个目录中，但特定目录中仅可具有一个提示文件。

不存在提示文件还是存在多个提示文件，你的项目将受此影响。 如果没有提示文件，则分析系统使用错误恢复技术来忽略无法辨认的源代码。 否则，分析系统使用以下策略查找和收集提示。

### <a name="search-order"></a>搜索顺序

分析系统按以下顺序在目录中搜索提示文件。

- 包含 Visual C++ 安装包 (vcpackages) 的目录。 此目录包含一个内置的提示文件，用于描述常用系统文件中的符号（如 windows.h）。 因此，项目会自动继承其所需的大部分提示。

- 从源文件根目录指向包含源文件本身的目录的路径。 在典型的 Visual C++ 项目中，根目录包含解决方案或项目文件。

   此规则的例外情况是“停止”文件位于源文件的路径中。 “停止”文件是任意名为 cpp.stop 的文件，可加强对搜索顺序的控制。 分析系统首先搜索的不是根目录，而是先搜索包含“停止”文件的目录，再逐一搜索到包含源文件的目录。 在典型的项目中，无需停止文件。

### <a name="hint-gathering"></a>提示收集

提示文件包含零个或多个提示。 提示的定义或删除方式与 C/C++ 宏一样。 也就是说，`#define` 预处理器指令用于创建或重新定义提示，`#undef` 指令用于删除提示。

分析系统按上述搜索顺序打开每个提示文件，将每个文件的提示累积到一组有效提示中，然后使用有效提示来解释代码中的标识符。

分析系统按以下规则来累积提示。

- 如果新提示指定了尚未定义的名称，则新提示将该名称添加到有效提示中。

- 如果新提示指定了已定义的名称，则新提示将重新定义现有提示。

- 如果新提示是指定现有有效提示的 `#undef` 指令，则新提示会删除现有提示。

第一条规则表示有效提示是从以前打开的提示文件中继承的。 后两条规则表示搜索顺序中稍后出现的提示可替代先前出现的提示。 例如，如果在包含源文件的目录中创建提示文件，则可替代以前的任何提示。

若要了解如何收集提示，请参阅本主题后面的 `Example` 部分。

### <a name="syntax"></a>语法

使用与创建和删除宏的预处理器指令相同的语法来创建和删除提示。 事实上，分析系统使用 C/C++ 预处理器来评估提示。 有关预处理器指令的详细信息，请参阅 [#define 指令 (C/C++)](../preprocessor/hash-define-directive-c-cpp.md) 和 [#undef 指令 (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md)。

唯一罕见的语法元素是 `@<``@=` 和 `@>` 替换字符串。 它们是提示文件特定的替换字符串，仅与 map 宏一起使用。 映射是将数据、函数或事件与其他数据、函数或事件处理程序相关联的一组宏。 例如，`MFC` 通过映射创建[消息映射](../mfc/reference/message-maps-mfc.md)，而 `ATL` 通过映射创建[对象映射](../atl/reference/object-map-macros.md)。 提示文件特定的替换字符串指示映射的开始、中间和结束元素。 只有映射宏的名称很重要。 因此，每个替换字符串都故意隐藏宏的实现。

提示使用以下语法。

|语法|含义|
|------------|-------------|
|`#define` *hint-name* *replacement-string*<br /><br /> `#define` *hint-name* `(` *parameter*, ...`)`*replacement-string*|定义新提示或重新定义现有提示的预处理器指令。 指令发出后，预处理器用替换字符串替换源代码中每次出现的提示名称。<br /><br /> 第二种语法形式定义类似函数的提示。 如果源代码中出现类似函数的提示，则预处理器首先使用源代码中的相应参数替换替换字符串中每次出现的参数，然后使用替换字符串替换提示名称。|
|`@<`|指示一组映射元素开始的提示文件特定的替换字符串。|
|`@=`|指示中间映射元素的提示文件特定的替换字符串。 一个映射可有多个映射元素。|
|`@>`|指示一组映射元素结束的提示文件特定的替换字符串。|
|`#undef` *hint-name*|删除现有提示的预处理器指令。 提示的名称由 hint-name 标识符提供。|
|`//` *comment*|单行注释。|
|`/*`*comment*`*/`|多行注释。|

## <a name="what-macros-require-a-hint"></a>哪些宏需要提示？

某些类型的宏可能会干扰分析系统。 本部分介绍会导致问题的宏类型，以及可创建问题解决方案的提示类型。

### <a name="disruptive-macros"></a>中断型宏

某些宏会导致分析系统误解源代码，但在不影响浏览体验的情况下可忽略它。 例如，源代码注释语言 ([SAL](../c-runtime-library/sal-annotations.md)) 宏解析为 C++ 属性，可帮助查找编程错误。 如果要在浏览代码时忽略 SAL 注释，可能需要创建隐藏注释的提示文件。

在以下源代码中，`FormatWindowClassName()` 函数的参数类型为 `PXSTR`，参数名称为 `szBuffer`。 但是，分析系统会将 `_Pre_notnull_` 和 `_Post_z_` SAL 注释误认为参数类型或参数名称。

**源代码：**

```cpp
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)
```

**策略：** Null 定义

在此情况下，策略将 SAL 注释视为不存在。 为此，请指定替换字符串为 NULL 的提示。 因此，分析系统忽略注释，且“类视图”浏览器不显示注释。 （Visual C++ 包含隐藏 SAL 注释的内置提示文件。）

**提示文件：**

```cpp.hint
#define _Pre_notnull_
```

### <a name="concealed-cc-language-elements"></a>隐藏的 C/C++ 语言元素

分析系统误解源代码的典型原因是宏隐藏了 C/C++ [标点符号](../cpp/punctuators-cpp.md)或[关键字](../cpp/keywords-cpp.md)令牌。 也就是说，宏可能包含一对标点符号的一半，例如 `<>`、`[]`、`{}` 和 `()`。

在以下源代码中，`START_NAMESPACE` 宏隐藏未配对的左大括号 (`{`)。

**源代码：**

```cpp
#define START_NAMESPACE namespace MyProject {
```

**策略：** 直接复制

如果宏的语义对浏览体验至关重要，请创建一个与宏相同的提示。 分析系统将该宏解析为提示文件中的定义。

请注意，如果源文件中的宏包含其他宏，则仅在有效提示集中已存在这些哄时，才对其进行解释。

**提示文件：**

```cpp.hint
#define START_NAMESPACE namespace MyProject {
```

### <a name="maps"></a>映射

映射由指定起始元素、结束元素和零个或多个中间元素的宏组成。 分析系统对映射进行错误解释，原因是 C/C++ 语言元素在所有映射宏中隐藏，且完整的 C/C++ 语句的语法分布在多个独立的宏中。

以下源代码定义了 `BEGIN_CATEGORY_MAP`、`IMPLEMENTED_CATEGORY` 和 `END_CATEGORY_MAP` 宏。

**源代码：**

```cpp
#define BEGIN_CATEGORY_MAP(x)\
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },
#define END_CATEGORY_MAP()\
   { _ATL_CATMAP_ENTRY_END, NULL } };\
   return( pMap ); }
```

**策略：** 识别映射元素

为映射的开始、中间（若有）和结束元素指定提示。 使用特殊映射替换字符串 `@<`、`@=` 和 `@>`。 有关详细信息，请参阅本主题中的 `Syntax` 一节。

**提示文件：**

```cpp.hint
// Start of the map.
#define BEGIN_CATEGORY_MAP(x) @<
// Intermediate map element.
#define IMPLEMENTED_CATEGORY( catid ) @=
// Intermediate map element.
#define REQUIRED_CATEGORY( catid ) @=
// End of the map.
#define END_CATEGORY_MAP() @>
```

### <a name="composite-macros"></a>复合宏

复合宏包含一种或多种混淆分析系统的宏类型。

以下源代码包含指定命名空间作用域开始的 `START_NAMESPACE` 宏和指定映射开始的 `BEGIN_CATEGORY_MAP` 宏。

**源代码：**

```cpp
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```

**策略：** 直接复制

为 `START_NAMESPACE` 和 `BEGIN_CATEGORY_MAP` 宏创建提示，然后为 `NSandMAP` 宏创建与前面源代码所示相同的提示。 如果复合宏只包含中断型宏和空格，可定义一个替换字符串为 NULL 定义的提示。

在此示例中，假定 `START_NAMESPACE` 已经具有本主题中 `Concealed C/C++ Language Elements` 子标题中所述的提示。 并假定 `BEGIN_CATEGORY_MAP` 具有先前在 `Maps` 中所述的提示。

**提示文件：**

```cpp.hint
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```

### <a name="inconvenient-macros"></a>不合适的宏

某些宏可由分析系统解释，但很难被源代码读取，因为宏很长或很复杂。 为方便阅读，可提供一个简化宏显示形式的提示。

**源代码：**

```cpp
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)
```

**策略：** 简化

创建一个显示更简单的宏定义的提示。

**提示文件：**

```cpp.hint
#define STDMETHOD(methodName) void* methodName
```

## <a name="example"></a>示例

以下示例说明如何从提示文件中累积提示。 本例中不使用“停止”文件。

下图显示了 Visual C++ 项目中的一些物理目录。 提示文件位于 `vcpackages`、`Debug``A1` 和 `A2` 目录中。

### <a name="hint-file-directories"></a>提示文件目录

![通用的以及项目特定的提示文件目录。](../ide/media/hintfile.png "提示文件")

### <a name="directories-and-hint-file-contents"></a>目录和提示文件内容

以下列表显示了此项目中包含提示文件的目录以及这些提示文件的内容。 `vcpackages` 目录提示文件中存在很多提示，此处仅列举一些。

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- 调试

    ```cpp.hint
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```

- A1

    ```cpp.hint
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```

- A2

    ```cpp.hint
    // A2
    #undef OBRACE
    #undef CBRACE
    ```

### <a name="effective-hints"></a>有效提示

下表列出了此项目中源文件的有效提示。

- 源文件：A1_A2_B.cpp

- 有效提示：

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    // Debug...
    #define RAISE_EXCEPTION(x) throw (x)
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    // ...Debug
    #define END_NAMESPACE }
    ```

以下注释适用于上述列表。

- 有效提示来自 `vcpackages`、`Debug``A1` 和 `A2` 目录。

- `Debug` 提示文件中的 #undef 指令删除了 `vcpackages` 目录提示文件中的 `#define _In_` 提示。

- `A1` 目录中的提示文件重新定义 `START_NAMESPACE`。

- `A2` 目录中的 `#undef` 提示删除了 `Debug` 目录提示文件中 `OBRACE` 和 `CBRACE` 的提示。

## <a name="see-also"></a>请参阅

[为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[#define 指令 (C/C++)](../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef 指令 (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md)<br>
[SAL 批注](../c-runtime-library/sal-annotations.md)<br>
[消息映射](../mfc/reference/message-maps-mfc.md)<br>
[消息映射宏](../atl/reference/message-map-macros-atl.md)<br>
[对象映射宏](../atl/reference/object-map-macros.md)