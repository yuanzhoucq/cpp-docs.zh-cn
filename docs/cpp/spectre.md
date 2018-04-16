---
title: "spectre |Microsoft 文档"
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b515d25d4818cf8b6213a37f3fe78df4f3882a69
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="spectre"></a>spectre

**Microsoft 专用**

告知编译器不要插入 Spectre 变体 1 推测执行屏障的函数的说明。

## <a name="syntax"></a>语法

> **__declspec( spectre(nomitigation) )**  

## <a name="remarks"></a>备注

[/Qspectre](../build/reference/qspectre.md)编译器选项将使编译器将插入推测执行屏障说明的分析表明存在 Spectre 变体 1 安全漏洞。 发出的特定说明取决于处理器。 这些说明应该对代码大小或性能的影响非常小，则表明可能存在你的代码不受漏洞，并且需要最高的性能。

专家分析可能确定函数不会从 Spectre 变体 1 边界检查绕过缺陷。 在这种情况下，禁止在生成缓解函数内的代码显示通过应用`__declspec(spectre(nomitigation))`至函数声明。

> [!CAUTION]
> **/Qspectre**推理执行屏障指令提供重要的安全保护，并对性能产生影响微不足道。 因此，我们建议您不要取消它们，但在以下罕见的情况下除外：函数的性能至关重要，并且已经知道函数是安全的。

## <a name="example"></a>示例

下面的代码演示如何使用`__declspec(spectre(nomitigation))`。

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

[__declspec](../cpp/declspec.md)  
[关键字](../cpp/keywords-cpp.md)  
[/Qspectre](../build/reference/qspectre.md)  
