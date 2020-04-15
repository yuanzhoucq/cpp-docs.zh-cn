---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: bc4736ce233ce026ecab9ef38ac8379466b5a0bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365587"
---
# <a name="safebuffers"></a>safebuffers

**微软特定**

告知编译器不要插入针对函数的缓冲区溢出安全检查。

## <a name="syntax"></a>语法

```
__declspec( safebuffers )
```

## <a name="remarks"></a>备注

**/GS**编译器选项通过在堆栈上插入安全检查，使编译器测试缓冲区溢出。 符合安全检查条件的数据结构类型在[/GS（缓冲区安全检查）中](../build/reference/gs-buffer-security-check.md)描述。 有关缓冲区溢出检测的详细信息，请参阅[MSVC 中的安全功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)。

专家手动代码评审或外部分析可能确定函数不会出现缓冲区溢出。 在这种情况下，可以通过将 **__declspec（安全缓冲区）** 关键字应用于函数声明来禁止对函数的安全检查。

> [!CAUTION]
> 缓冲区安全检查提供了重要的安全保护，并且对性能的影响微不足道。 因此，我们建议您不要取消它们，但在以下罕见的情况下除外：函数的性能至关重要，并且已经知道函数是安全的。

## <a name="inline-functions"></a>内联函数

*主函数*可以使用[内联](inline-functions-cpp.md)关键字插入*辅助函数*的副本。 如果将 **__declspec（安全缓冲区）** 关键字应用于函数，则该函数将抑制缓冲区溢出检测。 但是，内联以下列方式影响 **__declspec（安全缓冲区）** 关键字。

假设为两个函数指定**了 /GS**编译器选项，但主函数指定 **__declspec（安全缓冲区）** 关键字。 辅助函数中的数据结构将使它符合安全检查的条件，因此该函数不会取消这些检查。 在这种情况下：

- 在辅助函数上指定[__forceinline](inline-functions-cpp.md)关键字，以强制编译器内联该函数，而不考虑编译器优化。

- 由于辅助函数符合安全检查条件，因此安全检查也会应用于主函数，即使它指定**了__declspec（安全缓冲区）** 关键字。

## <a name="example"></a>示例

以下代码演示如何使用 **__declspec（安全缓冲区）** 关键字。

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

**结束微软特定**

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[Keywords](../cpp/keywords-cpp.md)<br/>
[内联、 __inline、_forceinline \_](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
