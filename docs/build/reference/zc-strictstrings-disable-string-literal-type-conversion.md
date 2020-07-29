---
title: /Zc:strictStrings（禁用字符串文本类型转换）
ms.date: 03/06/2018
f1_keywords:
- /Zc:strictStrings
- strictStrings
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
ms.openlocfilehash: df880ed64fa472ff55eb5ee0d17caacf56228ab6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211887"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>`/Zc:strictStrings`（禁用字符串文本类型转换）

当指定时，编译器需要严格 **`const`** 限定的一致性来实现使用字符串文本初始化的指针。

## <a name="syntax"></a>语法

> **`/Zc:strictStrings`**[**`-`**]

## <a name="remarks"></a>备注

如果 **`/Zc:strictStrings`** 指定了，则编译器将针对字符串文本强制实施标准 c + + **`const`** 限定，类型为 "数组 of" `const char` 或 "array of `const wchar_t` "，具体取决于声明。 字符串文本不可变，并且尝试修改一个字符串文本的内容将导致在运行时出现访问冲突错误。 必须声明字符串指针 **`const`** ，使其通过使用字符串文本进行初始化，或使用显式 **`const_cast`** 初始化非 **`const`** 指针。 默认情况下，如果 **`/Zc:strictStrings-`** 指定了，则编译器不会对 **`const`** 使用字符串文本初始化的字符串指针强制实施标准 c + + 限定。

**`/Zc:strictStrings`** 默认情况下，此选项处于关闭状态。 [`/permissive-`](permissive-standards-conformance.md)编译器选项隐式设置此选项，但可以使用重写它 **`/Zc:strictStrings-`** 。

使用 **`/Zc:strictStrings`** 选项可防止编译错误的代码。 此示例显示一个简单声明错误如何在运行时导致崩溃：

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

**`/Zc:strictStrings`** 启用时，相同的代码会在的声明中报告错误 `str` 。

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

如果使用 **`auto`** 声明字符串指针，编译器将为您创建正确的 **`const`** 指针类型声明。 编译器将修改指针内容的尝试 **`const`** 报告为错误。

> [!NOTE]
> Visual Studio 2013 中的 c + + 标准库不支持 **`/Zc:strictStrings`** 调试版本中的编译器选项。 如果在生成输出中看到几个[C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md)错误，则这可能是原因。

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 修改 "**附加选项**" 属性以包含 **`/Zc:strictStrings`** ，然后选择 **"确定"**。

## <a name="see-also"></a>另请参阅

[`/Zc`度](zc-conformance.md)<br/>
