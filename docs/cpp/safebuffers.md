---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: 456e84cfba40a4219f44fe1549272621f79d09a2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213237"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft 专用**

告知编译器不要插入针对函数的缓冲区溢出安全检查。

## <a name="syntax"></a>语法

```
__declspec( safebuffers )
```

## <a name="remarks"></a>备注

**/Gs**编译器选项导致编译器通过在堆栈上插入安全检查来测试缓冲区溢出。 [/Gs （缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)中介绍了符合安全检查条件的数据结构类型。 有关缓冲区溢出检测的详细信息，请参阅[MSVC 中的安全功能](https://devblogs.microsoft.com/cppblog/security-features-in-microsoft-visual-c/)。

专家手动代码评审或外部分析可能确定函数不会出现缓冲区溢出。 在这种情况下，可以通过将 **`__declspec(safebuffers)`** 关键字应用于函数声明来禁止对函数进行安全检查。

> [!CAUTION]
> 缓冲区安全检查提供了重要的安全保护，并且对性能的影响微不足道。 因此，我们建议您不要取消它们，但在以下罕见的情况下除外：函数的性能至关重要，并且已经知道函数是安全的。

## <a name="inline-functions"></a>内联函数

*主函数*可以使用[内联](inline-functions-cpp.md)关键字插入*辅助函数*的副本。 如果将 **`__declspec(safebuffers)`** 关键字应用于函数，则会取消该函数的缓冲区溢出检测。 不过，内联会 **`__declspec(safebuffers)`** 以下列方式影响关键字。

假设为这两个函数指定了 **/gs**编译器选项，但主函数指定了 **`__declspec(safebuffers)`** 关键字。 辅助函数中的数据结构将使它符合安全检查的条件，因此该函数不会取消这些检查。 在这种情况下：

- 对辅助函数指定[__forceinline](inline-functions-cpp.md)关键字可强制编译器内联该函数，而不考虑编译器优化。

- 由于辅助函数有资格进行安全检查，因此即使指定关键字，安全检查也会应用于主函数 **`__declspec(safebuffers)`** 。

## <a name="example"></a>示例

下面的代码演示如何使用 **`__declspec(safebuffers)`** 关键字。

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
