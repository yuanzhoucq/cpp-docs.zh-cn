---
title: 链接器工具错误 LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: 706cf6c90dc187b6c343edc82cebb93bb8660452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194845"
---
# <a name="linker-tools-error-lnk1561"></a>链接器工具错误 LNK1561

必须定义入口点

链接器找不到*入口点*，初始函数将在可执行文件中调用。 默认情况下，链接器将查找适用于控制台应用程序的 `main` 或 `wmain` 函数、Windows 应用程序的 `WinMain` 或 `wWinMain` 函数，或用于需要初始化的 DLL 的 `DllMain`。 您可以通过使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项来指定另一个函数。

此错误可能有几个原因：
- 您可能没有在要链接的文件列表中包含定义入口点的文件。 验证包含入口点函数的文件是否已链接到您的应用程序中。
- 您可能已使用错误的函数签名定义了入口点;例如，您可能对函数名称拼写错误或使用了错误的大小写，或者错误地指定了返回类型或参数类型。
- 生成 DLL 时，可能未指定[/DLL](../../build/reference/dll-build-a-dll.md)选项。
- 当你使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项时，你可能已指定了入口点函数的名称不正确。
- 如果使用[LIB](../../build/reference/lib-reference.md)工具生成 DLL，则可能已指定 .def 文件。 如果是这样，请从生成中删除 .def 文件。

生成应用时，链接器将查找用于启动代码的入口点函数。 这是在加载应用并初始化运行时调用的函数。 必须提供应用的入口点函数，否则应用无法运行。 对于 DLL，入口点是可选的。 默认情况下，链接器将查找具有多个特定名称和签名之一的入口点函数，如 `int main(int, char**)`。 您可以通过使用/ENTRY 链接器选项将其他函数名称指定为入口点。

## <a name="example"></a>示例

下面的示例生成 LNK1561：

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
