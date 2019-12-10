---
title: 链接器工具错误 LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: fe64eecfbc9fed57c3748afd5804b76d6e4284a4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990934"
---
# <a name="linker-tools-error-lnk1301"></a>链接器工具错误 LNK1301

找到 LTCG clr 模块，与/LTCG： parameter 不兼容

使用/clr 和/GL 编译的模块以及/LTCG. 的按配置优化（PGO）参数之一传递到链接器

对于/clr 模块，不支持按配置优化。

有关详细信息，请参阅：

- [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG（链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)

- [/cgthreads（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)

- [按配置文件优化](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>更正此错误

1. 不要用/clr 编译，或不要链接到/LTCG. 中的某个 PGO 参数

## <a name="example"></a>示例

下面的示例生成 LNK1301：

```cpp
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```
