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
ms.openlocfilehash: afd05e7380ec3838fe9763be23ccfae338adb4fb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220262"
---
# <a name="import-directive-c"></a>#import 指令（C++）

**C++相关**

过去一直合并类型库中的信息。 类型库的内容将转换为 C++ 类，主要描述 COM 接口。

## <a name="syntax"></a>语法

> **#import**"*filename*" \[*特性*] \
> **#import**\< *filename*特性]> \[

### <a name="parameters"></a>参数

*名字*\
指定要导入的类型库。 *文件名*可以是以下类型之一：

- 包含类型库的文件的名称，如 .olb、.tlb 或 .dll 文件。 关键字`file:`可以位于每个文件名之前。

- 类型库中控件的 progid。 关键字`progid:`可以在每个 progid 之前。 例如:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   有关 progid 的详细信息，请参阅[指定本地化 ID 和版本号](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)。

   在64位操作系统上使用32位交叉编译器时，编译器只能读取32位注册表配置单元。 您可能需要使用本机 64 位编译器才能生成和注册 64 位类型库。

- 类型库的库 ID。 关键字`libid:`可以在每个库 ID 之前。 例如:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   如果未指定`version`或 `lcid`，则应用于`progid:`的[规则](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)也应用于`libid:`。

- 可执行 (.exe) 文件。

- 包含类型库资源（例如 .ocx）的库（.dll）文件。

- 包含类型库的复合文档。

- 可由**LoadTypeLib** API 理解的任何其他文件格式。

*属性*\
一个或多个[#import 特性](#_predir_the_23import_directive_import_attributes)。 用空格或逗号分隔每个特性。 例如:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\- 或 -

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>备注

### <a name="_predir_the_23import_directive_searchorderforfilename"></a>文件名的搜索顺序

*filename*前面有一个目录规范。 文件名必须命名现有文件。 两种语法形式之间的差异在于预处理器在未完整指定路径时搜索类型库文件的顺序。

|语法形式|操作|
|-----------------|------------|
|带引号的形式|指示预处理器首先在包含 **#import**语句的文件目录中查找类型库文件，然后在包含文件的任何文件`#include`的目录中查找。 然后预处理器沿如下所示的路径执行搜索。|
|尖括号形式|指示预处理器沿下列路径搜索类型库文件：<br /><br /> 1.`PATH`环境变量路径列表<br />2.`LIB`环境变量路径列表<br />3.由[/i](../build/reference/i-additional-include-directories.md)编译器选项指定的路径，但编译器正在搜索从另一个类型库引用的类型库，该类型库具有[no_registry](../preprocessor/no-registry.md)特性。|

### <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>指定本地化 ID 和版本号

指定 progid 时，还可以指定 progid 的本地化 ID 和版本号。 例如：

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

如果未指定本地化 ID，将根据以下规则选择 progid：

- 如果只有一个本地化 ID，则使用该 ID。

- 如果有多个本地化 ID，则使用版本号为0、9或409的第一个本地化 ID。

- 如果有多个本地化 ID，而它们都不是0、9或409，则使用最后一个。

- 如果未指定版本号，则使用最新版本。

###  <a name="_predir_the_23import_directive_header_files_created_by_import"></a>通过导入创建的头文件

**#import**创建两个标头文件，用于在源代码中C++重新构造类型库内容。 主头文件类似于 Microsoft 接口定义语言（MIDL）编译器生成的文件，但具有其他编译器生成的代码和数据。 [主头文件](#_predir_the_primary_type_library_header_file)与类型库具有相同的基名称，再加上.TLH 扩展。 次头文件具有与类型库相同的基名称以及 .TLI 扩展。 它包含编译器生成的成员函数的实现，并且包含 (`#include`) 在主头文件中。

如果导入使用`byref`参数的调度接口属性， **#import**不会生成该函数的[__declspec （property）](../cpp/property-cpp.md)语句。

这两个标头文件都放置在由[/fo （name object file）](../build/reference/fo-object-file-name.md)选项指定的输出目录中。 然后，编译器将读取和编译它们，就像主头文件由`#include`指令命名一样。

以下编译器优化与 **#import**指令一起提供：

- 头文件在创建后将给定与类型库相同的时间戳。

- 处理 **#import**时，编译器首先检查标头是否存在并且是最新的。 如果是，则无需重新创建。

**#Import**指令也参与最小重新生成并可放置在预编译头文件中。  有关详细信息，请参阅[创建预编译头文件](../build/creating-precompiled-header-files.md)。

### <a name="_predir_the_primary_type_library_header_file"></a>主类型库头文件

主类型库头文件包含 7 个部分：

- 标题样板：包含 comdef.h 的注释`#include`和语句。H （定义在标头中使用的一些标准宏）和其他杂项设置信息。

- 前向引用和 typedef：由结构声明（例如`struct IMyInterface`和 typedef）组成。

- 智能指针声明：模板类`_com_ptr_t`是智能指针。 它封装了接口指针，无需调用`AddRef`、 `Release`和`QueryInterface`函数。 它还会在`CoCreateInstance`创建新的 COM 对象时隐藏调用。 本部分使用宏语句`_COM_SMARTPTR_TYPEDEF`将 COM 接口的 typedef 建立为[_com_ptr_t](../cpp/com-ptr-t-class.md)模板类的模板专用化。 例如，对于接口`IMyInterface`，为.TLH 文件将包含：

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   编译器可将其扩展为：

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   然后类型 `IMyInterfacePtr` 可以代替原始的接口指针 `IMyInterface*` 使用。 因此，无需调用各种`IUnknown`成员函数

- Typeinfo 声明：主要由类定义和其他项组成，这些项公开了返回`ITypeLib:GetTypeInfo`的各个 typeinfo 项。 在本节中，类型库中每个 typeinfo 都会反映在标头中，具体形式取决于 `TYPEKIND` 信息。

- 可选的旧样式 GUID 定义：包含命名 GUID 常量的初始化。 这些名称的形式与`CLSID_CoClass` MIDL `IID_Interface`编译器生成的格式相同。

- 用于次要类型库标头的 `#include` 语句。

- 页脚样本：目前包括`#pragma pack(pop)`。

除标题样本和页脚样本部分之外的所有部分都括在命名空间中，其名称由原始 IDL `library`文件中的语句指定。 可以通过使用命名空间名称的显式限定来使用类型库标头中的名称。 或者，可以包含以下语句：

```cpp
using namespace MyLib;
```

紧跟在源代码中的 **#import**语句之后。

可以通过使用 **#import**指令的[no_namespace](no-namespace.md)）特性来禁止显示命名空间。 但是，禁止显示命名空间可能会导致名称冲突。 命名空间也可以通过[rename_namespace](rename-namespace.md)属性重命名。

编译器提供当前正在处理的类型库所需的任何类型库依赖项的完整路径。 路径是以注释形式写入编译器为每个已处理的类型库生成的类型库标头 (.TLH) 中的。

如果类型库包括对其他类型库中所定义类型的引用，则 .TLH 文件将包括下列顺序的注释：

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

**#Import**注释中的实际文件名为交叉引用类型库的完整路径，存储在注册表中。 如果遇到因丢失类型定义而导致的错误，请检查的开头的注释.TLH 查看可能需要首先导入哪些依赖类型库。 错误可能是语法错误（例如，C2143、C2146、C2321）、C2501（缺少声明说明符）或者编译 .TLI 时的 C2433（数据声明上不允许“inline”）。

若要解决依赖项错误，请确定系统标头不会提供哪些依赖项注释，然后在依赖类型库的 **#import**指令之前的某个位置提供 **#import**指令。

### <a name="_predir_the_23import_directive_import_attributes"></a>#import 特性

**#import**可以选择包括一个或多个属性。 这些特性通知编译器修改类型库标头的内容。 反斜杠（ **\\** ）符号可用于在单个 **#import**语句中包含附加行。 例如:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

有关详细信息，请参阅[#import 特性](../preprocessor/hash-import-attributes-cpp.md)。

**结束C++特定**

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)\
[编译器 COM 支持](../cpp/compiler-com-support.md)
