---
title: 链接器工具警告 LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: 43ed18808ba5ce632dd7dc7095f7bc30e4497ec9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2019
ms.locfileid: "59674222"
---
# <a name="linker-tools-warning-lnk4286"></a>链接器工具警告 LNK4286

> 符号*符号*中定义*filename_1.obj*导入*filename_2.obj*

[__declspec （dllimport)](../../cpp/dllexport-dllimport.md)为指定*符号*即使对象文件中定义了符号*filename_1.obj*中相同的映像。 删除`__declspec(dllimport)`修饰符来解决此警告。

## <a name="remarks"></a>备注

警告 LNK4286 是更一般的版本[链接器工具警告 LNK4217](linker-tools-warning-lnk4217.md)。 链接器生成警告 LNK4286 时它可以告知所引用的对象文件的符号，但不是哪个函数。

若要解决 LNK4286，删除`__declspec(dllimport)`中的前向声明声明修饰符*符号*中引用*filename_2.obj*。

虽然最终生成的代码的行为正确，但生成调用导入的函数的代码是效率低于直接调用该函数。 通过使用编译时不会出现此警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项。

有关导入和导出数据声明上的详细信息，请参阅[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="see-also"></a>请参阅

[链接器工具警告 LNK4049](linker-tools-warning-lnk4049.md) \
[链接器工具警告 LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)