---
title: 'main: 程序启动'
ms.date: 11/04/2016
f1_keywords:
- vc.main.startup
- _tmain
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
ms.openlocfilehash: 29e1b77c2e36c66e4e6fc4ec30a73af4d57654a0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857432"
---
# <a name="main-program-startup"></a>main: 程序启动

名为**main**的特殊函数是所有 C 和C++程序的开始执行点。 如果要编写符合 Unicode 编程模型的代码，则可以使用 `wmain`，这是**main**的宽字符版本。

编译器未预定义**main**函数。 必须在程序文本中提供此函数。

**Main**的声明语法为

```cpp
int main();
```

或（可选）

```cpp
int main(int argc, char *argv[], char *envp[]);
```

**Microsoft 专用**

`wmain` 的声明语法如下所示：

```cpp
int wmain( );
```

或（可选）

```cpp
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

你还可以使用 tchar 中定义的 `_tmain`。 `_tmain` 解析为**main** ，除非定义了 _UNICODE。 在该示例中，`_tmain` 将解析为 `wmain`。

或者，可以将**main**和 `wmain` 函数声明为返回**void** （无返回值）。 如果将**main**或 `wmain` 声明为返回**void**，则不能使用[return](../cpp/return-statement-in-program-termination-cpp.md)语句将退出代码返回到父进程或操作系统。 若要在**main**或 `wmain` 声明为**void**时返回退出代码，则必须使用[exit](../cpp/exit-function.md)函数。

**结束 Microsoft 专用**

`argc` 和 `argv` 的类型由语言定义。 名称 `argc`、`argv` 和 `envp` 是传统的，但编译器不需要这些名称。 有关详细信息和示例，请参阅[自变量定义](../cpp/argument-definitions.md)。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[使用 wmain 代替 main](../cpp/using-wmain-instead-of-main.md)<br/>
[main 函数限制](../cpp/main-function-restrictions.md)<br/>
[分析 C++ 命令行参数](../cpp/parsing-cpp-command-line-arguments.md)
