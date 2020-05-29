---
title: 使用 __declspec(dllimport) 导入函数调用
description: 在调用 DLL 数据和函数时使用 _declspec(dllimport) 的操作方法及原因。
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765716"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>使用 `__declspec(dllimport)` 导入函数调用

使用 `__declspec(dllimport)` 可以更快地对调用添加批注  。 访问导出的 DLL 数据始终需要 `__declspec(dllimport)` 。

## <a name="import-a-function-from-a-dll"></a>导入 DLL 中的函数

以下代码示例演示如何使用 `__declspec(dllimport)` 将 DLL 中的函数调用导入到应用程序中  。 假设 `func1` 是一个函数，该函数位于与包含 main 函数的可执行文件分开的 DLL 中  。

如果没有 `__declspec(dllimport)`，则给定以下代码  ：

```C
int main(void)
{
   func1();
}
```

编译器生成如下所示的代码：

```asm
call func1
```

链接器将调用转换为如下所示的内容：

```asm
call 0x4000000         ; The address of 'func1'.
```

如果 `func1` 位于另一个 DLL 中，则链接器无法直接解析此地址，因为它无法知道 `func1` 的地址。 在 32 位和 64 位环境中，链接器在已知地址中生成 thunk。 在 32 位环境中 thunk 如下所示：

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

此处 `__imp_func1` 是可执行文件的导入地址表中 `func1` 槽的地址。 链接器已知道所有这些地址。 加载程序只需在加载时更新可执行文件的导入地址表，即可使所有操作正常运行。

这就是使用 `__declspec(dllimport)` 更好的原因：因为链接器在不需要时不会生成 thunk  。 Thunk 使代码变大（在 RISC 系统上，它可以是多个指令），并可能降低缓存性能。 如果告诉编译器函数位于 DLL 中，则可以为你生成间接调用。

现在此代码：

```C
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

生成此指令：

```asm
call DWORD PTR __imp_func1
```

没有 thunk 和 `jmp` 指令，因此代码很小且速度更快。 可以通过使用全程序优化，在没有 `__declspec(dllimport)` 的情况下获得相同的效果  。 有关详细信息，请参阅 [/GL（全程序优化）](reference/gl-whole-program-optimization.md)。

对于 DLL 中的函数调用，不需要使用间接调用。 链接器已知道函数的地址。 在间接调用之前加载和存储函数的地址需要额外的时间和空间。 直接调用速度更快且所需空间更小。 从 DLL 本身的外部调用 DLL 函数时，只需使用 `__declspec(dllimport)` 。 生成 DLL 时，不使用 DLL 内的函数上的 `__declspec(dllimport)` 。

## <a name="see-also"></a>请参阅

[导入到应用程序中](importing-into-an-application.md)
