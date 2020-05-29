---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 9ede0d3b53c975298dea3d1331bc0fb00ac246b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328248"
---
# <a name="exports"></a>EXPORTS

引入了一个由一个或多个导出定义组成的节，这些定义可指定函数或数据的导出名或序号。 每个定义必须在单独一行上。

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>备注

第一个*定义*可以与`EXPORTS`关键字位于同一行上，也可以位于后续行上。 .DEF 文件可以包含一个或多个 `EXPORTS` 语句。

导出*定义的*语法是：

> *条目名称*\[__=__*internal_name* \[ **\@** \[ \[ \[ **PRIVATE** _ordinal_ **NONAME***other_module.exported_name*other_module.exported_name = 二级 NONAME = 私有 ||\[**数据**|

*项名称*是要导出的函数或变量名称。 这是必填字段。 如果导出的名称与 DLL 中的名称不同，请使用*internal_name*在 DLL 中指定导出的名称。 例如，如果 DLL 导出函数 `func1`，并且你希望调用方将其用作 `func2`，则应指定：

```DEF
EXPORTS
   func2=func1
```

如果导出的名称来自其他模块，请使用*other_module.exported_name*在 DLL 中指定导出的名称。 例如，如果 DLL 导出函数 `other_module.func1`，并且你希望调用方将其用作 `func2`，则应指定：

```DEF
EXPORTS
   func2=other_module.func1
```

如果导出的名称来自由位元导出的另一个模块，请使用*other_module*在 DLL 中指定导出的元号。__#__ *ddinal*. 例如，如果 DLL 从具有正项 42 的其他模块导出函数，并且希望调用方将其用作`func2`，则可以指定：

```DEF
EXPORTS
   func2=other_module.#42
```

由于 MSVC 编译器使用名称修饰C++函数，因此必须使用修饰名称*internal_name，* 或者使用源代码`extern "C"`定义导出的函数。 编译器还修饰 C 函数，这些函数使用[__stdcall](../../cpp/stdcall.md)调用约定，其\_前缀和后缀由 at sign （\@） 组成，后跟参数列表中的字节数（十进制）。

要查找编译器生成的修饰名称，请使用[DUMPBIN](dumpbin-reference.md)工具或链接器[/MAP](map-generate-mapfile.md)选项。 修饰名特定于编译器。 如果要将修饰名导出到 .DEF 文件中，则链接到 DLL 的可执行文件也必须通过使用同一版本的编译器生成。 这可确保调用方中的修饰名与 .DEF 文件中的导出名相匹配。

可以使用\@ *ddinal*指定数字（而不是函数名称）进入 DLL 的导出表。 许多 Windows DLL 将导出序号以支持旧版代码。 通常使用采用 16 位 Windows 编码的序号，因为这有助于最大程度地减小 DLL 的大小。 我们不建议通过元代导出函数，除非您的 DLL 客户需要它来提供旧版支持。 由于 .LIB 文件将包含序号与函数之间的映射，因此你可以像通常在使用 DLL 的项目中那样使用函数名。

通过使用可选的**NONAME**关键字，您只能按位数导出，并减小生成的 DLL 中的导出表的大小。 但是，如果要在 DLL 上使用[GetProcAddress，](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)您必须知道序号，因为名称无效。

可选关键字**PRIVATE**可防止*条目名称*包含在 LINK 生成的导入库中。 它不会影响同样是由 LINK 生成的映像中的导出。

可选关键字**DATA**指定导出是数据，而不是代码。 此示例显示如何导出名为 `exported_global` 的数据变量：

```DEF
EXPORTS
   exported_global DATA
```

可通过采用建议的顺序列出的四种方式导出定义：

1. 源代码中的[__declspec（dllexport）](../../cpp/dllexport-dllimport.md)关键字

1. .DEF 文件中的 `EXPORTS` 语句

1. LINK 命令中的[/EXPORT](export-exports-a-function.md)规范

1. 窗体[comment](../../preprocessor/comment-c-cpp.md)`#pragma comment(linker, "/export: definition ")`中的注释指令。 下面的示例在函数声明之前显示#pragma注释指令，其中`PlainFuncName`未修饰的名称是`_PlainFuncName@4`函数的修饰名称：

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

如果需要导出未修饰的函数名称，并且根据生成配置（例如，在 32 位或 64 位生成中）具有不同的导出，则#pragma指令非常有用。

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

## <a name="see-also"></a>另请参阅

[模块定义语句的规则](rules-for-module-definition-statements.md)
