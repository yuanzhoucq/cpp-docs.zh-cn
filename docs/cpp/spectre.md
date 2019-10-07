---
title: spectre
ms.date: 01/23/2018
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
ms.openlocfilehash: 40eee25dec867ae3fce7a6b2d4715f0be81bfe76
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926371"
---
# <a name="spectre"></a>spectre

**Microsoft 专用**

告诉编译器不要插入函数的 Spectre 变体1推理执行关卡说明。

## <a name="syntax"></a>语法

> **__declspec( spectre(nomitigation) )**

## <a name="remarks"></a>备注

[/Qspectre](../build/reference/qspectre.md)编译器选项将导致编译器插入推理执行关卡说明。 它们是在分析表明存在 Spectre 变体1安全漏洞的位置插入的。 发出的具体说明取决于处理器。 尽管这些说明对代码大小或性能的影响最小，但在某些情况下，你的代码不受此漏洞的影响，并且需要最高的性能。

专家分析可能会确定函数从 Spectre 变体1界限检查绕过缺陷中是安全的。 在这种情况下，可以通过将应用`__declspec(spectre(nomitigation))`到函数声明来禁止在函数内生成缓解代码。

> [!CAUTION]
> **/Qspectre**推理执行屏障指令提供重要的安全保护，对性能的影响可以忽略不计。 因此，我们建议您不要取消它们，但在以下罕见的情况下除外：函数的性能至关重要，并且已经知道函数是安全的。

## <a name="example"></a>示例

下面的代码演示如何使用 `__declspec(spectre(nomitigation))`。

```cpp
// compile with: /c /Qspectre
static __declspec(spectre(nomitigation))
int noSpectreIssues() {
    // No Spectre variant 1 vulnerability here
    // ...
    return 0;
}

int main() {
    noSpectreIssues();
    return 0;
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[/Qspectre](../build/reference/qspectre.md)
