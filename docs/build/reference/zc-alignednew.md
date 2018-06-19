---
title: /Zc:alignedNew （c + + 17 过度对齐的分配） |Microsoft 文档
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:alignedNew
dev_langs:
- C++
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
author: corob-msft
ms.author: corob
ms.openlocfilehash: 5f9527d63a9843bd4df90520e5b4759126d72fe1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378375"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew （c + + 17 过度对齐的分配）

支持 C + + 17 过度对齐**新**，动态内存分配在大于最大大小标准对齐类型，默认的边界上对齐**max\_对齐\_t**.

## <a name="syntax"></a>语法

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>备注

Visual Studio 版本 15.5 使编译器和 C + + 17 标准过度对齐动态内存分配的库支持。 当 **/Zc:alignedNew**指定选项，如动态分配`new Example;`遵循的对齐方式*示例*甚至当其大于`max_align_t`，最大对齐所需的任何基本类型。 当分配的类型的对齐方式只是为原始运算符可以确保获得**新**、 可用的预定义的宏的值作为 **\_ \_STDCPP\_默认\_新建\_对齐\_\_**，语句`new Example;`对的调用会导致`::operator new(size_t)`像在 C + + 14 中。 当对齐大于 **\_ \_STDCPP\_默认\_新建\_对齐\_\_**，实现改为获取通过使用内存`::operator new(size_t, align_val_t)`。 同样，删除过度对齐的类型时，将调用`::operator delete(void*, align_val_t)`或大小删除签名`::operator delete(void*, size_t, align_val_t)`。

**/Zc:alignedNew**选项才可用[/std:c + + 17](std-specify-language-standard-version.md)或[/std:c + + 最新](std-specify-language-standard-version.md)已启用。 下 **/std:c + + 17**或 **/std:c + + 最新**， **/Zc:alignedNew**默认启用以符合 ISO C + + 17 标准。 如果你的唯一原因实现运算符**新**和**删除**是支持过度对齐的分配，你可能不再需要此代码在 C + + 17 模式下。 若要关闭此选项并恢复到 C + + 14 的行为**新**和**删除**时 **/std::c + + 17**或 **/std:c + + 最新**指定，则指定 **/Zc:alignedNew-**。 如果实现运算符**新**和**删除**但你不准备实现过度对齐的运算符**新**和**删除**具有重载`align_val_t`参数，使用 **/Zc:alignedNew-** 选项以阻止生成的编译器和标准库调用过度对齐的重载。 [/ 宽松-](permissive-standards-conformance.md)选项不会更改的默认设置 **/Zc:alignedNew**。

## <a name="example"></a>示例

此示例演示如何运算符**新**和运算符**删除**时行为 **/Zc:alignedNew**设置选项。

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

此输出是典型的 32 位版本。 应用程序运行在内存中基于的指针值会不同。

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Visual c + + 中一致性问题的信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/Zc:alignedNew**或 **/Zc:alignedNew-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](../../build/reference/zc-conformance.md)  
