---
title: '/Zc: referencebinding （强制引用绑定规则）'
ms.date: 03/06/2018
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
ms.openlocfilehash: 9dfe8f5b4713d9567f6e98af6685c552fb51160e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316101"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc: referencebinding （强制引用绑定规则）

当 **/zc: referencebinding**指定选项，编译器不允许将绑定到一个临时的非常量左值引用。

## <a name="syntax"></a>语法

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>备注

如果 **/zc: referencebinding**指定，则编译器遵循标准的 C + + 11 8.5.3 部分并且不允许将临时的用户定义类型绑定到非常数 lvalue 引用的表达式。 默认情况下，或者如果 **/Zc:referenceBinding-** 指定，编译器允许此类表达式作为 Microsoft 扩展，但不会产生 4 级警告。 代码安全性、 可移植性和符合性，我们建议你使用 **/zc: referencebinding**。

**/Zc: referencebinding**选项默认情况下处于关闭状态。 [触发-](permissive-standards-conformance.md)编译器选项隐式设置此选项，但它可以通过重写 **/Zc:referenceBinding-**。

## <a name="example"></a>示例

此示例显示允许用户定义类型的临时绑定到的非常量左值引用的 Microsoft 扩展。

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

void main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/zc: referencebinding** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/Zc（一致性）](zc-conformance.md)<br/>
