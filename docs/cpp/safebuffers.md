---
title: safebuffers |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- safebuffers_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6590a2f210156711066fac241170103cc5a8830
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034351"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft 专用**

告知编译器不要插入针对函数的缓冲区溢出安全检查。

## <a name="syntax"></a>语法

```
__declspec( safebuffers )
```

## <a name="remarks"></a>备注

**/GS**编译器选项将使编译器通过插入在堆栈上的安全检查来测试缓冲区溢出。 中介绍了符合安全检查的条件的数据结构的类型[/GS （缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)。 有关缓冲区溢出检测的详细信息，请参阅[MSVC 中的安全功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)。

专家手动代码评审或外部分析可能确定函数不会出现缓冲区溢出。 在这种情况下，可以通过应用取消安全检查的函数 **__declspec （safebuffers)** 函数声明的关键字。

> [!CAUTION]
>  缓冲区安全检查提供了重要的安全保护，并且对性能的影响微不足道。 因此，我们建议您不要取消它们，但在以下罕见的情况下除外：函数的性能至关重要，并且已经知道函数是安全的。

## <a name="inline-functions"></a>内联函数

一个*主要功能*可以使用[内联](inline-functions-cpp.md)关键字来插入一份*辅助函数*。 如果 **__declspec （safebuffers)** 关键字应用于函数，缓冲区溢出检测取消对该函数。 但是，内联，影响 **__declspec （safebuffers)** 以下方面的关键字。

假设 **/GS**编译器选项指定对于这两个函数，但主函数指定 **__declspec （safebuffers)** 关键字。 辅助函数中的数据结构将使它符合安全检查的条件，因此该函数不会取消这些检查。 这种情况下：

- 指定[__forceinline](inline-functions-cpp.md)辅助函数可强制编译器内联到该函数而不考虑编译器优化的关键字。

- 由于辅助函数符合安全检查的条件，安全检查也应用于的主要功能即使它指定 **__declspec （safebuffers)** 关键字。

## <a name="example"></a>示例

下面的代码演示如何使用 **__declspec （safebuffers)** 关键字。

```cpp
// compile with: /c /GS
typedef struct {
    int x[20];
} BUFFER;
static int checkBuffers() {
    BUFFER cb;
    // Use the buffer...
    return 0;
};
static __declspec(safebuffers)
    int noCheckBuffers() {
    BUFFER ncb;
    // Use the buffer...
    return 0;
}
int wmain() {
    checkBuffers();
    noCheckBuffers();
    return 0;
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[inline、__inline、\__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)