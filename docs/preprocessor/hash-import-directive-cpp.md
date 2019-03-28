---
title: '#导入指令 （c + +）'
ms.date: 03/27/2019
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
ms.openlocfilehash: 72fd1d025ab19b7db9521e08655d00936b77581e
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564948"
---
# <a name="import-directive-c"></a>#import 指令 (C++)

**C + + 专用**

过去一直合并类型库中的信息。 类型库的内容将转换为 C++ 类，主要描述 COM 接口。

## <a name="syntax"></a>语法

```
#import "filename" [attributes]
#import <filename> [attributes]
```

### <a name="parameters"></a>参数

*filename*<br/>
指定要导入的类型库。 *文件名*可以是以下之一：

- 包含类型库的文件的名称，如 .olb、.tlb 或 .dll 文件。 关键字**文件：**，每个文件名之前可以放置。

- 类型库中控件的 progid。 关键字**progid:**，之前可以放置每个 progid。 例如：

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   有关 progid 的详细信息，请参阅[指定本地化 ID 和版本号](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)。

   请注意，在 64 位操作系统上使用交叉编译器编译时，该编译器只能读取 32 位注册表配置单元。 您可能需要使用本机 64 位编译器才能生成和注册 64 位类型库。

- 类型库的库 ID。 关键字**libid:**，可以位于之前，每个库 id。 例如：

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   如果未指定版本或 lcid，[规则](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)应用于**progid:** 也适用于**libid:**。

- 可执行 (.exe) 文件。

- 包含类型库资源（例如 .ocx）的库 (.dll) 文件。

- 包含类型库的复合文档。

- 可以理解的任何其他文件格式**LoadTypeLib** API。

*特性*<br/>
一个或多个[#import 属性](#_predir_the_23import_directive_import_attributes)。 用空格或逗号分隔每个特性。 例如：

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\- 或 -

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>备注

## <a name="_predir_the_23import_directive_searchorderforfilename"></a> 文件名的搜索顺序

*文件名*后可跟目录规范。 文件名必须命名现有文件。 两种语法形式之间的差异在于预处理器在未完整指定路径时搜索类型库文件的顺序。

|语法形式|操作|
|-----------------|------------|
|带引号的形式|指示预处理器，若要查找的类型库文件中包含的文件的目录的第 **#import**语句，然后在包括任何文件的目录 (`#include`) 该文件。 然后预处理器沿如下所示的路径执行搜索。|
|尖括号形式|指示预处理器沿下列路径搜索类型库文件：<br /><br /> 1.`PATH`环境变量路径列表<br />2.`LIB`环境变量路径列表<br />3./I 指定的路径 (附加包含目录) 编译器选项，只不过它使用的另一个类型库从引用的类型库中搜索编译器[no_registry](../preprocessor/no-registry.md)属性。|

##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> 指定本地化 ID 和版本号

指定 progid 时，还可以指定 progid 的本地化 ID 和版本号。 例如：

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

如果未指定本地化 ID，则根据下列规则选择 progid：

- 如果只有一个本地化 ID，则使用这一个。

- 如果有多个本地化 ID，则使用版本号为 0、9 或 409 的第一个本地化 ID。

- 如果有多个本地化 ID，而它们都不为 0、9 或 409，则使用最后一个本地化 ID。

- 如果未指定版本号，则使用最新版本。

##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> 创建导入的标头文件

**#import**创建两个标头文件以重新构造 c + + 源代码中的类型库内容。 主头文件类似于 Microsoft 接口定义语言 (MIDL) 编译器生成的文件，但具有附加的编译器生成的代码和数据。 [主头文件](#_predir_the_primary_type_library_header_file)与类型库具有相同的基名称加上。TLH 扩展。 次头文件具有与类型库相同的基名称以及 .TLI 扩展。 它包含编译器生成的成员函数的实现，并且包含 (`#include`) 在主头文件中。

如果导入使用 byref 参数的调度接口属性，#import 将不会生成 __declspec ([属性](../cpp/property-cpp.md)) 函数的语句。

两个头文件都放置在 /Fo（名称对象文件）选项指定的输出目录中。 然后它们由编译器进行读取和编译，就像 `#include` 指令命名主头文件一样。

下列编译器优化伴随 **#import**指令：

- 头文件在创建后将给定与类型库相同的时间戳。

- 当 **#import**是处理，编译器首先会检查标头存在并且保持最新。 如果是，则不需要重新创建。

**#Import**指令也参与最小重新生成，并可以放置在预编译标头文件。 请参阅[创建预编译标头文件](../build/creating-precompiled-header-files.md)有关详细信息。

###  <a name="_predir_the_primary_type_library_header_file"></a> 主类型库标头文件
主类型库头文件包含 7 个部分：

- 标题样本：包含注释、 `#include` COMDEF 的语句。H （它定义的标头中使用的一些标准宏），和其他杂项安装信息。

- 前向引用和 typedef:包含结构声明如`struct IMyInterface`和 typedef。

- 智能指针声明：此模板类`_com_ptr_t`是封装接口指针，并且不需要调用的智能指针实现`AddRef`， `Release`，`QueryInterface`函数。 此外，它在创建新的 COM 对象时会隐藏 `CoCreateInstance` 调用。 本部分使用宏语句`_COM_SMARTPTR_TYPEDEF`若要将模板专用化的 COM 接口的 typedef 建立[_com_ptr_t](../cpp/com-ptr-t-class.md)模板类。 例如，对于接口`IMyInterface`、。TLH 文件将包含：

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   编译器可将其扩展为：

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   然后类型 `IMyInterfacePtr` 可以代替原始的接口指针 `IMyInterface*` 使用。 因此，则无需调用各种`IUnknown`成员函数

- Typeinfo 声明：主要包含类定义和公开返回的各个 typeinfo 项的其他项`ITypeLib:GetTypeInfo`。 在本节中，类型库中每个 typeinfo 都会反映在标头中，具体形式取决于 `TYPEKIND` 信息。

- 可选旧式 GUID 定义：包含名为 GUID 常量的初始化。 这些是窗体的名称`CLSID_CoClass`和`IID_Interface`，类似于那些由 MIDL 编译器生成。

- 用于次要类型库标头的 `#include` 语句。

- 页脚样本：当前包括`#pragma pack(pop)`。

除标题样本和页脚样本部分之外的所有部分的命名空间中都包含指定其名称`library`原始 IDL 文件中的语句。 您可使用类型库标头的名称，方法是通过显式限定命名空间名称或通过包括以下语句：

```cpp
using namespace MyLib;
```

后立即 **#import**的源代码中的语句。

命名空间可通过使用抑制[no_namespace](no-namespace.md)) 的属性 **#import**指令。 但是，禁止显示命名空间可能会导致名称冲突。 此外可以通过重命名命名空间[rename_namespace](rename-namespace.md)属性。

编译器提供了至其当前处理的类型库所需的任何类型库依赖项的完整路径。 路径是以注释形式写入编译器为每个已处理的类型库生成的类型库标头 (.TLH) 中的。

如果类型库包括对其他类型库中所定义类型的引用，则 .TLH 文件将包括下列顺序的注释：

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

中的实际文件名 **#import**注释是交叉引用的类型库的完整路径，如存储在注册表中。 如果由于缺少类型定义遇到错误，请检查位于 .TLH 头处的注释来了解需要先导入的依赖类型库。 错误可能是语法错误（例如，C2143、C2146、C2321）、C2501（缺少声明说明符）或者编译 .TLI 时的 C2433（数据声明上不允许“inline”）。

您必须确定哪些依赖项的注释否则不由系统标头提供的然后提供 **#import**指令之前的某个时刻 **#import**指令的从属项若要解决这些错误的类型库。

## <a name="_predir_the_23import_directive_import_attributes"></a> #import 属性

**#import**可以选择性地包含一个或多个属性。 这些特性通知编译器修改类型库标头的内容。 反斜杠 (**\\**) 符号可以用于在单个包含附加行 **#import**语句。 例如：

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

有关详细信息，请参阅[#import 属性](../preprocessor/hash-import-attributes-cpp.md)。

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)<br/>
[编译器 COM 支持](../cpp/compiler-com-support.md)