---
title: /Zc:alignedNew （c + + 17 过度对齐的分配）
ms.date: 02/28/2018
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: e0d850d54611579288b81a334af4abdfab6e411c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820333"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew （c + + 17 过度对齐的分配）

启用对 C + + 17 过度对齐的支持**新**，动态内存分配大于最大尺寸标准对齐类型，默认值的边界上对齐**max\_对齐\_t**.

## <a name="syntax"></a>语法

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>备注

Visual Studio 版本 15.5 使编译器和 C + + 17 标准过度对齐的动态内存分配的库支持。 当 **/Zc:alignedNew**指定选项，如动态分配`new Example;`尊重的对齐方式*示例*甚至时大于`max_align_t`的最大对齐所需的任何基本类型。 当已分配类型的对齐方式只是为保证由原始运算符的**新**，可作为预定义的宏的值 **\_ \_STDCPP\_默认\_新建\_对齐\_\_**，该语句`new Example;`对的调用会导致`::operator new(size_t)`像在 C + + 14 中。 当的对齐方式是大于 **\_ \_STDCPP\_默认\_新建\_对齐\_\_**，实现改为获取通过使用内存`::operator new(size_t, align_val_t)`。 同样，删除的过对齐类型调用`::operator delete(void*, align_val_t)`或固定大小的删除签名`::operator delete(void*, size_t, align_val_t)`。

**/Zc:alignedNew**选项才可用[/std: c + + 17](std-specify-language-standard-version.md)或[/std: c + + 最新](std-specify-language-standard-version.md)已启用。 下 **/std: c + + 17**或 **/std: c + + 最新**， **/Zc:alignedNew**默认情况下启用符合 ISO C + + 17 标准。 如果您的唯一原因实现运算符**新**并**删除**是支持过度对齐的分配，可能不再需要此代码在 C + + 17 模式下。 若要关闭此选项，并恢复到 C + + 14 的行为**新**并**删除**时 **/std::c + + 17**或 **/std: c + + 最新**指定，则指定 **/zc:**。 如果实现运算符**新**并**删除**但你已准备好实施过度对齐的运算符**新**并**删除**具有的重载`align_val_t`参数，请使用 **/zc:** 选项以阻止编译器和标准库生成调用到过度对齐的重载。 [触发-](permissive-standards-conformance.md)选项不会更改的默认设置 **/Zc:alignedNew**。

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

此输出是典型的 32 位版本。 在内存中运行应用程序基于的指针的值会有所不同。

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Visual c + + 中一致性问题的信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/Zc:alignedNew**或 **/zc:** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)
