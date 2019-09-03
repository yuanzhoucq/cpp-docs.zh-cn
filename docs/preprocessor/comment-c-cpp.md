---
title: 注释杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: 3175ad5318bcc6fd9aa6233258ccec9033c89be8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219095"
---
# <a name="comment-pragma"></a>注释杂注

将注释记录置于对象文件或可执行文件中。

## <a name="syntax"></a>语法

> **#pragma 注释 (** *comment-type* [ **,** "*comment-string*"] **)**

## <a name="remarks"></a>备注

*Comment 类型*是预定义的标识符之一, 如下所述, 指定注释记录的类型。 可选的*注释字符串*是提供某些注释类型附加信息的字符串文字。 因为*注释字符串*是字符串文字, 所以它服从与转义符、嵌入引号 (`"`) 和串联相关的字符串文字的所有规则。

### <a name="compiler"></a>编译器

将编译器的名称和版本号置于对象文件中。 此注释记录将被链接器忽略。 如果为此记录类型提供*注释字符串*参数, 编译器将生成警告。

### <a name="lib"></a>lib

将库搜索记录置于对象文件中。 此注释类型必须附带一个*注释字符串*参数, 该参数包含希望链接器搜索的库的名称 (也可能是路径)。 库名称遵循对象文件中的默认库搜索记录;链接器会搜索此库, 就像你在命令行上命名此库, 前提是未在[/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md)中指定库。 可以将多个库搜索记录置于同一个源文件中；各个记录将以其在源文件中显示的顺序出现在对象文件中。

如果默认库和添加的库的顺序很重要, 使用[/zl](../build/reference/zl-omit-default-library-name.md)开关进行编译将阻止将默认库名称放置在对象模块中。 然后，可使用另一个注释杂注在添加的库的后面插入默认库的名称。 与这些杂注一起列出的库将以其在源代码中的发现顺序出现在对象模块中。

### <a name="linker"></a>链接器

将[链接器选项](../build/reference/linker-options.md)放在对象文件中。 可以使用注释类型来指定链接器选项，而不是将其传递到命令行或在开发环境中指定它。 例如，可以指定 /include 选项来强制包含符号：

```C
#pragma comment(linker, "/include:__mySymbol")
```

仅可将以下 (*注释类型*) 链接器选项传递给链接器标识符:

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>user

将一般注释置于对象文件中。 *Comment 字符串*参数包含注释的文本。 此注释记录将被链接器忽略。

## <a name="examples"></a>示例

以下杂注会促使链接器在链接时搜索 EMAPI.LIB 库。 链接器首先在当前工作目录中搜索，然后在 LIB 环境变量指定的路径中搜索。

```C
#pragma comment( lib, "emapi" )
```

以下杂注会促使编译器将其名称和版本号置于对象文件中：

```C
#pragma comment( compiler )
```

对于采用*注释字符串*参数的注释, 可以在使用字符串文字的任何位置使用宏, 前提是该宏扩展到字符串文字。 您还可以字符串与扩展到字符串的宏的任意组合串联在一起。 例如，以下语句是可接受的：

```C
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
