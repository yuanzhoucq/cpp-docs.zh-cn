---
title: 使用 __declspec(dllimport) 导入函数调用
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 8635cf5d389f72972f471a4fd53ed56c3497bfe9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811727"
---
# <a name="importing-function-calls-using-declspecdllimport"></a>使用 __declspec(dllimport) 导入函数调用

下面的代码示例演示如何使用 **_declspec(dllimport)** 函数调用从 DLL 导入到应用程序。 假定`func1`是驻留在单独的.exe 文件中包含的 DLL 函数**主**函数。

无需 **__declspec （dllimport)**，给定此代码：

```
int main(void)
{
   func1();
}
```

编译器将生成如下所示的代码：

```
call func1
```

和链接器将转换到类似以下调用：

```
call 0x4000000         ; The address of 'func1'.
```

如果`func1`存在于另一个 DLL，链接器不能直接解析因为它有没有办法知道的地址`func1`是。 在 16 位环境中，链接器将此代码地址添加到在运行时使用正确的地址加载程序将修补程序的.exe 文件中的列表。 在 32 位和 64 位环境中，链接器生成它的其中知道地址转换 （thunk）。 在 32 位环境中转换 （thunk） 如下所示：

```
0x40000000:    jmp DWORD PTR __imp_func1
```

这里`imp_func1`的地址是`func1`槽中的.exe 文件的导入地址表。 链接器就知道所有地址。 仅加载程序必须在一切就会正常工作负载时，更新的.exe 文件导入地址表。

因此，使用 **__declspec （dllimport)** 比较好，因为链接器不会生成一个 thunk，如果不需要。 Thunk 使代码更大 （RISC 在系统上，它可以是几种指令），可以降低缓存性能。 如果您告知编译器该函数是在 DLL 中，它可为你生成的间接调用。

因此，现在此代码：

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

生成此指令：

```
call DWORD PTR __imp_func1
```

没有任何转换 （thunk），但不`jmp`指令，因此该代码是更小更快。

但是，对于 DLL 内部的函数调用，您不要必须使用间接调用。 您已经知道函数的地址。 由于需要时间和空间以加载和存储之前的间接调用函数的地址，直接调用始终是更快、 更小。 您只想要使用 **__declspec （dllimport)** 时调用从 DLL 本身的外部的 DLL 函数。 不要使用 **__declspec （dllimport)** 上生成该 DLL 时的 DLL 中的函数。

## <a name="see-also"></a>请参阅

[导入到应用程序中](importing-into-an-application.md)
