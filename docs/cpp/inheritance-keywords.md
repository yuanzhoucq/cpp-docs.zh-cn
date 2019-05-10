---
title: 继承关键字
ms.date: 11/04/2016
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
ms.openlocfilehash: 656ee7ed38c24c9f3b8881f84d8e33ca81e3d936
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183487"
---
# <a name="inheritance-keywords"></a>继承关键字

**Microsoft 专用**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

其中：

*class-name*<br/>
要声明的类的名称。

C++ 允许您在类定义前声明指向类成员的指针。 例如：

```cpp
class S;
int S::*p;
```

在上面的代码，`p`被声明为指向类 s。 整数成员的指针但是，`class S`具有尚未定义在此代码中; 它只声明。 当编译器遇到此类指针时，它必须生成此指针的泛化表示形式。 表示形式的大小依赖于指定的继承模型。 可通过四种方式指定编译器的继承模型：

- 在 IDE 中**指向成员的指针表示形式**

- 在命令行中使用[/vmg](../build/reference/vmb-vmg-representation-method.md)切换

- 使用[pointers_to_members](../preprocessor/pointers-to-members.md)杂注

- 使用继承关键字 **__single_inheritance**， **__multiple_inheritance**，并 **__virtual_inheritance**。 此技术控制每个类的继承模型。

    > [!NOTE]
    >  如果在定义类后始终声明指向类成员的指针，则无需使用上述任何选项。

在类定义之前声明一个指向类成员的指针会影响生成的可执行文件的大小和速度。           类使用的继承越复杂，表示指向此类成员的指针所需的字节数以及解释指针所需的代码数就越大。 单一继承的复杂性最低，虚拟继承的复杂性最高。

如果将上面的示例更改为：

```cpp
class __single_inheritance S;
int S::*p;
```

无论命令行选项或杂注如何，指向 `class S` 的成员的指针都将使用可能的最小表示形式。

> [!NOTE]
>  类的指向成员的指针表示形式的同一向前声明应出现在声明指向该类的成员的指针的每个翻译单元中，并且声明应在声明指向成员的指针之前出现。

与以前版本的兼容性 **_single_inheritance**， **_multiple_inheritance**，并 **_virtual_inheritance**是同义词的 **__单继承**， **__multiple_inheritance**，和 **__virtual_inheritance**除非编译器选项[/Za\(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md)指定。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)