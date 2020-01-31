---
title: /Zc:referenceBinding（强制引用绑定规则）
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
ms.openlocfilehash: b7e297d6fd913ddda4d44a42298a361e314af0b5
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518473"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding（强制引用绑定规则）

指定 **/zc： referenceBinding**选项时，编译器不允许将非 const lvalue 引用绑定到临时。

## <a name="syntax"></a>语法

> **/Zc:referenceBinding**[ **-** ]

## <a name="remarks"></a>备注

如果指定了 **/zc： referenceBinding** ，则编译器将遵循 c + + 11 标准的8.5.3 节：它不允许将用户定义类型的表达式临时绑定到非常量左值引用。 默认情况下，或者如果指定了 **/zc： referenceBinding** ，编译器将允许此类表达式作为 Microsoft 扩展，但会发出第4级警告。 为了实现代码安全性、可移植性和一致性，我们建议使用 **/zc： referenceBinding**。

默认情况下， **/zc： referenceBinding**选项处于关闭状态。 [/Permissive-](permissive-standards-conformance.md)编译器选项隐式设置此选项，但可以使用 **/zc： referenceBinding-** 进行重写。

## <a name="example"></a>示例

此示例显示允许将用户定义类型的临时绑定到非常量左值引用的 Microsoft 扩展。

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

int main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “C/C++” > “命令行”属性页。

1. 修改 "**附加选项**" 属性以包含 **/zc： referenceBinding** ，然后选择 **"确定"** 。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/Zc（一致性）](zc-conformance.md)<br/>
