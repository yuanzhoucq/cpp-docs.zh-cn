---
title: /Zc:alignedNew（C++17 过度对齐的分配）
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: 041f62bbbf5f7a2750960d21d1534cf6daf4b874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335685"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew（C++17 过度对齐的分配）

启用对 C++17 过度对齐的 new 的支持，它是一种在大于最大标准对齐类型 max\_align\_t 的默认值的边界对齐的动态内存分配********。

## <a name="syntax"></a>语法

> **/Zc：对齐新**\[-*

## <a name="remarks"></a>备注

MSVC 编译器和库支持 C++17 标准过度对齐的动态内存分配。 指定 **/Zc：对齐New**选项时，动态分配（如如表示`new Example;`*）表示"示例*"的对齐方式，即使它大于`max_align_t`，则表示任何基本类型所需的最大对齐方式。 当分配的类型的对齐不超过原始运算符**new**保证的对齐方式时，该语句作为预定义的宏**\_\_STDCPP\_DEFAULT\_NEW\_对齐\_** 的值可用，该语句`new Example;`会导致调用`::operator new(size_t)`，就像在 C++14 中所做的那样。 当对齐大于**\_\_STDCPP\_DEFAULT\_新\_对齐\_时**，实现将改为使用`::operator new(size_t, align_val_t)`获取内存。 同样，删除过度对齐的类型会调用 `::operator delete(void*, align_val_t)` 或特定大小的删除签名 `::operator delete(void*, size_t, align_val_t)`。

/Zc:alignedNew 选项仅在启用了 [/std:c++17](std-specify-language-standard-version.md) 或 [/std:c++latest](std-specify-language-standard-version.md) 时才可用****。 在 /std:c++17 或 /std:c++latest 下，默认启用 /Zc:alignedNew，以符合 ISO C++17 标准************。 如果你实现运算符 new 和 delete 的唯一原因是支持过度对齐的分配，则在 C++17 模式中可能不再需要此代码********。 若要关闭此选项，并在使用 /std::c++17 或 /std:c++latest 时还原为 new 和 delete 的 C++14 行为，请指定 /Zc:alignedNew-********************。 如果实现运算符 new 和 delete，但未准备好实现具有 `align_val_t` 参数的过度对齐的运算符 new 和 delete 重载，请使用 /Zc:alignedNew- 选项防止编译器和标准库生成对过度对齐的重载的调用********************。 [/permissive-](permissive-standards-conformance.md) 选项不会更改 /Zc:alignedNew 的默认设置****。

从 Visual Studio 2017 版本 15.5 开始，提供对 /Zc:alignedNew 的支持****。

## <a name="example"></a>示例

此示例演示在设置了 /Zc:alignedNew 选项时，运算符 new 和运算符 delete 的行为如何************。

```cpp
// alignedNew.cpp
// Compile by using: cl /EHsc /std:c++17 /W4 alignedNew.cpp
#include <iostream>
#include <malloc.h>
#include <new>

// "old" unaligned overloads
void* operator new(std::size_t size) {
    auto ptr = malloc(size);
    std::cout << "unaligned new(" << size << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size) {
    std::cout << "unaligned sized delete(" << ptr << ", " << size << ")\n";
    free(ptr);
}

void operator delete(void* ptr) {
    std::cout << "unaligned unsized delete(" << ptr << ")\n";
    free(ptr);
}

// "new" over-aligned overloads
void* operator new(std::size_t size, std::align_val_t align) {
    auto ptr = _aligned_malloc(size, static_cast<std::size_t>(align));
    std::cout << "aligned new(" << size << ", " <<
        static_cast<std::size_t>(align) << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size, std::align_val_t align) {
    std::cout << "aligned sized delete(" << ptr << ", " << size <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

void operator delete(void* ptr, std::align_val_t align) {
    std::cout << "aligned unsized delete(" << ptr <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

struct alignas(256) OverAligned {}; // warning C4324, structure is padded

int main() {
    delete new int;
    delete new OverAligned;
}
```

对于 32 位版本来说，此输出非常典型。 指针值根据应用程序在内存中运行的不同位置而有所不同。

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

有关 Visual C++ 中一致性问题的信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/C++** > **命令行**属性页。

1. 修改“附加选项”属性以包含 /Zc:alignedNew 或 /Zc:alignedNew-，然后选择“确定”****************。

## <a name="see-also"></a>另请参阅

[/Zc（一致性）](zc-conformance.md)
