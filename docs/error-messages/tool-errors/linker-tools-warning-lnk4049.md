---
title: 链接器工具警告 LNK4049 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4049
dev_langs:
- C++
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ad4e4adb492789639c71a25a2db774a80cd77c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021754"
---
# <a name="linker-tools-warning-lnk4049"></a>链接器工具警告 LNK4049

本地定义的符号 symbol 导入

符号同时从导出和导入到该程序。

通过使用声明一个符号时，链接器会生成此警告`__declspec(dllexport)`存储类特性在一个对象文件和使用引用`__declspec(dllimport)`中另一个属性。

警告 LNK4049 是更一般的版本[链接器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)。 链接器生成警告 LNK4049 时它不能确定从哪个函数引用的导入的符号。

其中 LNK4049 生成而不是 LNK4217 的常见情形是：

- 执行使用增量链接[/incremental](../../build/reference/incremental-link-incrementally.md)选项。

- 通过使用执行全程序优化[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)选项。

若要解决 LNK4049，请尝试以下项之一：

- 删除`__declspec(dllimport)`名称从触发 LNK4049 的符号的前向声明的声明。 可以使用的二进制映像中的符号搜索**DUMPBIN**实用程序。 **DUMPBIN/符号**开关显示的图像的 COFF 符号表。 有关详细信息**DUMPBIN**实用程序，请参阅[DUMPBIN 参考](../../build/reference/dumpbin-reference.md)。

- 临时禁用增量链接和全程序优化。 重新编译应用程序将生成警告 LNK4217，将包含从其引用的导入的符号的函数的名称。 删除`__declspec(dllimport)`从导入的符号和启用增量链接或全程序优化所需的声明。

虽然最终生成的代码就能正常工作，但生成调用导入的函数的代码是效率低于直接调用该函数。 通过使用选项进行编译时不会出现此警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。

有关导入和导出数据声明上的详细信息，请参阅[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="example"></a>示例

链接以下两个模块将生成 LNK4049。 第一个模块将生成一个包含单个导出的函数对象文件。

```
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

## <a name="example"></a>示例

第二个模块将生成一个包含第一个模块，以及对在此函数的调用中导出的函数的前向声明的对象文件`main`函数。 链接的第一个模块使用此模块将生成 LNK4049。 删除`__declspec(dllimport)`声明将解决此警告。

```
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>请参阅

[链接器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)