---
title: 链接器工具警告 LNK4049
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: b527d15310dba70c1bae21e601db17db2900e219
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59674248"
---
# <a name="linker-tools-warning-lnk4049"></a>链接器工具警告 LNK4049

> 符号*符号*中定义*filename.obj*导入

[__declspec （dllimport)](../../cpp/dllexport-dllimport.md)为指定*符号*即使对象文件中定义了符号*filename.obj*中相同的映像。 删除`__declspec(dllimport)`修饰符来解决此警告。

## <a name="remarks"></a>备注

一个对象文件中定义符号，并使用引用时，链接器会生成此警告`__declspec(dllimport)`中另一个声明修饰符。

警告 LNK4049 是更一般的版本[链接器工具警告 LNK4217](linker-tools-warning-lnk4217.md)。 链接器生成警告 LNK4049 时它不能确定哪些函数或对象的文件引用的导入的符号。

其中 LNK4049 生成而不是 LNK4217 的常见情形是：

- 使用时[/incremental](../../build/reference/incremental-link-incrementally.md)选项。

- 使用时[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)选项。

若要解决 LNK4049，请尝试以下过程之一：

- 删除`__declspec(dllimport)`从触发 LNK4049 的符号的前向声明修饰符。 可以使用的二进制映像中的符号搜索**DUMPBIN**实用程序。 **DUMPBIN /SYMBOLS**开关显示的图像的 COFF 符号表。 有关详细信息**DUMPBIN**实用程序，请参阅[DUMPBIN 参考](../../build/reference/dumpbin-reference.md)。

- 临时禁用增量链接和全程序优化。 重新编译时，应用程序将生成警告 LNK4217，其中包括引用的导入的符号的函数的名称。 删除`__declspec(dllimport)`从导入的符号和重新启用增量链接或全程序优化所需的声明修饰符。

虽然最终生成的代码的行为正确，但生成调用导入的函数的代码是效率低于直接调用该函数。 通过使用编译时不会出现此警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项。

有关导入和导出数据声明上的详细信息，请参阅[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="example"></a>示例

链接以下两个模块将生成 LNK4049。 第一个模块将生成一个包含单个导出的函数对象文件。

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

第二个模块将生成一个包含第一个模块，以及对在此函数的调用中导出的函数的前向声明的对象文件`main`函数。 链接的第一个模块使用此模块将生成 LNK4049。 删除`__declspec(dllimport)`从声明要解决此警告的修饰符。

```cpp
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

[链接器工具警告 LNK4217](linker-tools-warning-lnk4217.md) \
[链接器工具警告 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)