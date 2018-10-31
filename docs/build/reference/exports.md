---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: b12548bafa9a0c580c5976cd7c4c54d8726e5ace
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435670"
---
# <a name="exports"></a>EXPORTS

引入了一个由一个或多个导出定义组成的节，这些定义可指定函数或数据的导出名或序号。 每个定义必须在单独一行上。

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>备注

第一个*定义*可以是同一行中还有`EXPORTS`关键字或后续行中。 .DEF 文件可以包含一个或多个 `EXPORTS` 语句。

导出的语法*定义*是：

> *entryname*\[__=__*internal_name*|*other_module.exported_name*] \[**\@**_序号_ \[ **NONAME**]] \[ \[**专用**] |\[**数据**]]

*entryname*是你想要导出的函数或变量名称。 这是必选项。 如果您导出的名称与 DLL 中名称不同，导出的 DLL 中通过使用指定名称*internal_name*。 例如，如果 DLL 导出函数 `func1`，并且你希望调用方将其用作 `func2`，则应指定：

```DEF
EXPORTS
   func2=func1
```

如果您导出的名称是从另一个模块，指定导出的名称在 DLL 中使用*other_module.exported_name*。 例如，如果 DLL 导出函数 `other_module.func1`，并且你希望调用方将其用作 `func2`，则应指定：

```DEF
EXPORTS
   func2=other_module.func1
```

如果从另一个按序号导出的模块导出的名称，指定导出的序号在 DLL 中使用*other_module*。__#__ *序号*。 例如，如果您的 DLL 导出函数，从其他模块，它是序号 42 和希望调用方将其用作`func2`，则会指定：

```DEF
EXPORTS
   func2=other_module.#42
```

因为 Visual c + + 编译器针对 c + + 函数使用名称修饰，您必须使用修饰的名*internal_name*或者通过使用定义导出的函数`extern "C"`的源代码中。 编译器还将修饰使用的 C 函数[__stdcall](../../cpp/stdcall.md)调用约定以下划线 (\_) 前缀和后缀组成 at 符号 (\@) 跟 in （采用十进制） 的字节数参数列表。

若要查找由编译器产生的修饰的名，请使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具或链接器[/map](../../build/reference/map-generate-mapfile.md)选项。 修饰名特定于编译器。 如果要将修饰名导出到 .DEF 文件中，则链接到 DLL 的可执行文件也必须通过使用同一版本的编译器生成。 这可确保调用方中的修饰名与 .DEF 文件中的导出名相匹配。

可以使用\@*序号*指定一个数字，而不是函数名称，将进入 DLL 的导出表。 许多 Windows DLL 将导出序号以支持旧版代码。 通常使用采用 16 位 Windows 编码的序号，因为这有助于最大程度地减小 DLL 的大小。 除非 DLL 的客户端需要按序号导出函数以支持旧版，否则我们不建议你执行此操作。 由于 .LIB 文件将包含序号与函数之间的映射，因此你可以像通常在使用 DLL 的项目中那样使用函数名。

通过使用可选**NONAME**关键字，可以只按序号导出并减小结果 DLL 中导出表的大小。 但是，如果你想要使用[GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress)上 DLL，您必须知道序号，因为名称将无效。

可选的关键字**私有**阻止*entryname*包括在由 LINK 生成的导入库中。 它不会影响同样是由 LINK 生成的映像中的导出。

可选的关键字**数据**指定导出的是数据，不是代码。 此示例显示如何导出名为 `exported_global` 的数据变量：

```DEF
EXPORTS
   exported_global DATA
```

可通过采用建议的顺序列出的四种方式导出定义：

1. [__Declspec （dllexport)](../../cpp/dllexport-dllimport.md)的源代码中的关键字

1. .DEF 文件中的 `EXPORTS` 语句

1. [/Export](../../build/reference/export-exports-a-function.md) LINK 命令中的规范

1. 一个[注释](../../preprocessor/comment-c-cpp.md)指令中的源代码的窗体`#pragma comment(linker, "/export: definition ")`。 下面的示例演示一个 #pragma 注释指令之前函数声明中，其中`PlainFuncName`是未修饰的名称，和`_PlainFuncName@4`是该函数的修饰的名：

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

#Pragma 指令很有用，如果你需要导出未修饰的函数名，并且具有不同的导出，具体取决于生成配置 （例如，在 32 位或 64 位版本）。

所有这四种方法可以用在同一个程序中。 LINK 在生成包含导出的程序时还创建导入库，除非生成中使用了 .EXP 文件。

下面是 EXPORTS 节的一个示例：

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

使用 .DEF 文件从 DLL 中导出变量时，不必在变量上指定 `__declspec(dllexport)`。 但是，在任何使用 DLL 的文件中，必须仍在数据的声明上使用 `__declspec(dllimport)`。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)
