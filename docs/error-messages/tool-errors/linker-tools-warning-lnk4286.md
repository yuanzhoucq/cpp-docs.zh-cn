---
title: 链接器工具警告 LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: d0205ba065f6e410383c38a0f1c2eaa0da55fe93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173863"
---
# <a name="linker-tools-warning-lnk4286"></a>链接器工具警告 LNK4286

> "*filename_1*" 中定义的符号 "*symbol*" 由 "*filename_2 .obj*" 导入

已为*符号*指定[__declspec （dllimport）](../../cpp/dllexport-dllimport.md) ，即使该符号是在同一映像的对象文件*filename_1*中定义的。 删除 `__declspec(dllimport)` 修饰符以解决此警告。

## <a name="remarks"></a>备注

警告 LNK4286 是更通用的[链接器工具警告 LNK4217](linker-tools-warning-lnk4217.md)版本。 当链接器可以判断哪个对象文件引用了符号而不是哪个函数时，链接器会生成警告 LNK4286。

若要解析 LNK4286，请从*filename_2 .obj*中引用*符号*的前向声明中删除 `__declspec(dllimport)` 声明修饰符。

尽管最终生成的代码的行为正确，但生成的用于调用导入函数的代码不如直接调用函数。 使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项编译时不会出现此警告。

有关导入和导出数据声明的详细信息，请参阅[dllexport、dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="see-also"></a>另请参阅

[链接器工具警告 LNK4049](linker-tools-warning-lnk4049.md) \
[链接器工具警告 LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)
