---
title: 导出 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- EXPORTS
dev_langs:
- C++
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cc7a9995fdc5be786712752e30015337b9f1607
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376821"
---
# <a name="exports"></a>EXPORTS
引入了一个由一个或多个导出定义组成的节，这些定义可指定函数或数据的导出名或序号。 每个定义必须在单独一行上。  
  
```  
EXPORTS  
   definition  
```  
  
## <a name="remarks"></a>备注  
 第一个 `definition` 可以和 `EXPORTS` 关键字在同一行或在下一行上。 .DEF 文件可以包含一个或多个 `EXPORTS` 语句。  
  
 导出 `definition` 的语法为：  
  
```  
  
entryname[=internalname] [@ordinal [NONAME]] [[PRIVATE] | [DATA]]  
```  
  
 `entryname` 是要导出的函数名或变量名。 这是必选项。 如果导出的名称与 DLL 中的名称不同，则使用 `internalname` 指定 DLL 中导出的名称。 例如，如果 DLL 导出函数 `func1`，并且你希望调用方将其用作 `func2`，则应指定：  
  
```  
EXPORTS  
   func2=func1  
```  
  
 由于 Visual C++ 编译器针对 C++ 函数使用名称修饰，因此你必须将修饰名用作 `entryname` 或 `internalname`，或在源代码中使用 `extern "C"` 定义导出函数。 编译器还将修饰使用的 C 函数[__stdcall](../../cpp/stdcall.md)调用约定带有下划线 (_) 前缀和组成的后缀 at 符号 (@) 后接参数列表中 （采用十进制） 的字节数。  
  
 若要查找由编译器生成的修饰的名，使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具或链接器[/映射](../../build/reference/map-generate-mapfile.md)选项。 修饰名特定于编译器。 如果要将修饰名导出到 .DEF 文件中，则链接到 DLL 的可执行文件也必须通过使用同一版本的编译器生成。 这可确保调用方中的修饰名与 .DEF 文件中的导出名相匹配。  
  
 可以使用 @`ordinal` 指定序号而不是函数名将进入 DLL 的导出表。 许多 Windows DLL 将导出序号以支持旧版代码。 通常使用采用 16 位 Windows 编码的序号，因为这有助于最大程度地减小 DLL 的大小。 除非 DLL 的客户端需要按序号导出函数以支持旧版，否则我们不建议你执行此操作。 由于 .LIB 文件将包含序号与函数之间的映射，因此你可以像通常在使用 DLL 的项目中那样使用函数名。  
  
 通过使用可选 `NONAME` 关键字，你可以只按序号导出，并减小结果 DLL 中导出表的大小。 但是，如果你想要使用[GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)在 DLL 上你必须知道序号，因为该名称将无效。  
  
 可选 `PRIVATE` 关键字禁止将 `entryname` 包含在由 LINK 生成的导入库中。 它不会影响同样是由 LINK 生成的映像中的导出。  
  
 可选 `DATA` 关键字指定导出的是数据，而不是代码。 此示例显示如何导出名为 `exported_global` 的数据变量：  
  
```  
EXPORTS  
   exported_global DATA  
```  
  
 可通过采用建议的顺序列出的四种方式导出定义：  
  
1.  [__Declspec （dllexport)](../../cpp/dllexport-dllimport.md)的源代码中的关键字  
  
2.  .DEF 文件中的 `EXPORTS` 语句  
  
3.  [/导出](../../build/reference/export-exports-a-function.md)LINK 命令中的规范  
  
4.  A[注释](../../preprocessor/comment-c-cpp.md)指令中的源代码，窗体 `#pragma comment(linker, "/export: definition ")`  
  
 所有这四种方法可以用在同一个程序中。 LINK 在生成包含导出的程序时还创建导入库，除非生成中使用了 .EXP 文件。  
  
 下面是 EXPORTS 节的一个示例：  
  
```  
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