---
title: '#import 指令 (C++)'
ms.date: 08/29/2019
f1_keywords:
- '#import'
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
ms.openlocfilehash: 9cdfef091b659151f427c381e386f0e83396e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332058"
---
# <a name="import-directive-c"></a>#import指令 （C++）

**C++ 专用**

过去一直合并类型库中的信息。 类型库的内容将转换为 C++ 类，主要描述 COM 接口。

## <a name="syntax"></a>语法

> **#import**"*文件名*"\[*属性*|
> **#import**\<*文件*> 名\[*属性*|

### <a name="parameters"></a>参数

*文件名*\
指定要导入的类型库。 *文件名*可以是以下类型之一：

- 包含类型库的文件的名称，如 .olb、.tlb 或 .dll 文件。 关键字 可以`file:`位于每个文件名之前。

- 类型库中控件的 progid。 关键字 ，`progid:`可以先于每个上位。 例如：

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   有关 progid 的更多，请参阅[指定本地化 ID 和版本号](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)。

   在 64 位操作系统上使用 32 位交叉编译器时，编译器只能读取 32 位注册表配置单元。 您可能需要使用本机 64 位编译器才能生成和注册 64 位类型库。

- 类型库的库 ID。 关键字 可以`libid:`位于每个库 ID 之前。 例如：

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   如果未指定`version``lcid`或 ，则应用于`progid:``libid:`[的规则](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)也会应用于 。

- 可执行 (.exe) 文件。

- 包含类型库资源（如 .ocx）的库 （.dll） 文件。

- 包含类型库的复合文档。

- **LoadTypeLib** API 可以理解的任何其他文件格式。

*属性*\
一个或多个[#import属性](#_predir_the_23import_directive_import_attributes)。 用空格或逗号分隔每个特性。 例如：

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\- 或 -

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>备注

### <a name="search-order-for-filename"></a><a name="_predir_the_23import_directive_searchorderforfilename"></a>搜索文件名的顺序

*文件名*在目录规范之前是可选的。 文件名必须命名现有文件。 两种语法形式之间的差异在于预处理器在未完整指定路径时搜索类型库文件的顺序。

|语法形式|操作|
|-----------------|------------|
|带引号的形式|指示预处理器首先在包含 **#import**语句的文件目录中查找类型库文件，然后在包含该文件`#include`的任何文件的目录中查找类型库文件。 然后预处理器沿如下所示的路径执行搜索。|
|尖括号形式|指示预处理器沿下列路径搜索类型库文件：<br /><br /> 1.`PATH`环境变量路径列表<br />2.`LIB`环境变量路径列表<br />3. [/I](../build/reference/i-additional-include-directories.md)编译器选项指定的路径，除了编译器正在搜索从具有[no_registry](../preprocessor/no-registry.md)属性的另一个类型库中引用的类型库。|

### <a name="specify-the-localization-id-and-version-number"></a><a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>指定本地化 ID 和版本号

指定 progid 时，还可以指定 progid 的本地化 ID 和版本号。 例如：

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

如果未指定本地化 ID，则根据以下规则选择 progid：

- 如果只有一个本地化 ID，则使用该 ID。

- 如果有多个本地化 ID，则使用版本号为 0、9 或 409 的第一个 ID。

- 如果有多个本地化 ID，并且它们都不是 0、9 或 409，则使用最后一个 ID。

- 如果不指定版本号，将使用最新版本。

### <a name="header-files-created-by-import"></a><a name="_predir_the_23import_directive_header_files_created_by_import"></a>导入创建的标头文件

**#import**创建两个标头文件，用于在C++源代码中重建类型库内容。 主标头文件类似于 Microsoft 接口定义语言 （MIDL） 编译器生成的文件，但具有其他编译器生成的代码和数据。 [主标头文件](#_predir_the_primary_type_library_header_file)具有与类型库相同的基本名称，外加 一个 。TLH 扩展。 次头文件具有与类型库相同的基名称以及 .TLI 扩展。 它包含编译器生成的成员函数的实现，并且包含 (`#include`) 在主头文件中。

如果导入使用`byref`参数的 dispinterface 属性 **，#import**不会为函数生成[__declspec（属性）](../cpp/property-cpp.md)语句。

两个头文件都放置在[/Fo（名称对象文件）](../build/reference/fo-object-file-name.md)选项指定的输出目录中。 然后，编译器读取和编译它们，就像主标头文件由指令命名一样`#include`。

#import**指令附带**了以下编译器优化：

- 头文件在创建后将给定与类型库相同的时间戳。

- 处理 **#import**时，编译器首先检查标头是否存在并且是最新的。 如果是，则无需重新创建。

**#import**指令还参与最少的重建，可以放置在预编译的标头文件中。  有关详细信息，请参阅[创建预编译的标头文件](../build/creating-precompiled-header-files.md)。

### <a name="primary-type-library-header-file"></a><a name="_predir_the_primary_type_library_header_file"></a>主类型库头文件

主类型库头文件包含 7 个部分：

- 标题样本：包含注释、COMDEF.H（定义标头中使用的一些标准宏）的 `#include` 语句和其他杂项安装信息。

- 转发引用和 typedef：包含结构声明（例如 `struct IMyInterface` 和 typedef）。

- 智能指针声明：模板类`_com_ptr_t`是智能指针。 它封装接口指针，并不需要调用`AddRef`和`Release``QueryInterface`函数。 在创建新的 COM`CoCreateInstance`对象时，它还隐藏调用。 本节使用宏语句`_COM_SMARTPTR_TYPEDEF`将 COM 接口的类型defs作为[_com_ptr_t](../cpp/com-ptr-t-class.md)模板类的模板专门化。 例如，对于接口`IMyInterface`， .TLH 文件将包含：

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   编译器可将其扩展为：

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   然后类型 `IMyInterfacePtr` 可以代替原始的接口指针 `IMyInterface*` 使用。 因此，无需调用各个`IUnknown`成员函数

- 类型信息声明：主要由类定义和其他项组成，公开 返回的`ITypeLib:GetTypeInfo`单个类型信息项。 在本节中，类型库中每个 typeinfo 都会反映在标头中，具体形式取决于 `TYPEKIND` 信息。

- 可选旧式 GUID 定义：包含名为 GUID 常量的初始化。 这些名称具有窗体`CLSID_CoClass`和`IID_Interface`，类似于 MIDL 编译器生成的名称。

- 用于次要类型库标头的 `#include` 语句。

- 页脚样本：当前包含 `#pragma pack(pop)`。

除标题样板和页脚样板部分外，所有部分都包含在命名空间中，其名称由原始 IDL`library`文件中的语句指定。 可以使用命名空间名称通过显式限定使用类型库标头中的名称。 或者，您可以包括以下语句：

```cpp
using namespace MyLib;
```

在源代码中 **#import**语句之后。

可以使用 **#import**指令的[no_namespace](no-namespace.md)） 属性来抑制命名空间。 但是，禁止显示命名空间可能会导致名称冲突。 命名空间也可以由[rename_namespace](rename-namespace.md)属性重命名。

编译器提供当前处理的类型库所需的任何类型的库依赖项的完整路径。 路径是以注释形式写入编译器为每个已处理的类型库生成的类型库标头 (.TLH) 中的。

如果类型库包括对其他类型库中所定义类型的引用，则 .TLH 文件将包括下列顺序的注释：

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

**#import**注释中的实际文件名是存储在注册表中的交叉引用类型库的完整路径。 如果遇到由于缺少类型定义而导致的错误，请检查 的注释在 。TLH 以查看可能需要首先导入哪些从属类型库。 错误可能是语法错误（例如，C2143、C2146、C2321）、C2501（缺少声明说明符）或者编译 .TLI 时的 C2433（数据声明上不允许“inline”）。

要解决依赖项错误，请确定系统标头未以其他方式提供哪些依赖项注释，然后在依赖类型库**的#import**指令之前的某个时间点提供 **#import**指令。

### <a name="import-attributes"></a><a name="_predir_the_23import_directive_import_attributes"></a>#import属性

**#import**可以选择包含一个或多个属性。 这些特性通知编译器修改类型库标头的内容。 反斜杠**\\**（ ） 符号可用于在单个 **#import**语句中包含其他行。 例如：

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

有关详细信息，请参阅[#import属性](../preprocessor/hash-import-attributes-cpp.md)。

**结束 C++ 专用**

## <a name="see-also"></a>另请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)\
[编译器 COM 支持](../cpp/compiler-com-support.md)
