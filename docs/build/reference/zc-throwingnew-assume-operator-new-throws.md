---
title: "/Zc:throwingNew （假定运算符新引发） |Microsoft 文档"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- throwingNew
- /Zc:throwingNew
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cbcb635cd37a40c2de1599d271658de308e8cff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew （假定运算符新引发）  
当`/Zc:throwingNew`指定选项，编译器优化对调用`operator new`跳过检查 null 指针返回。 此选项，可以告诉编译器假定所有链接的实现`operator new`和自定义分配器符合 c + + 标准和分配失败时引发。 默认情况下，在 Visual Studio 中，编译器将保守地生成 null 检查 (`/Zc:throwingNew-`) 为这些调用，因为用户可以将链接的非引发实现`operator new`或编写自定义分配器例程返回 null 指针。  
  
## <a name="syntax"></a>语法  
  
`/Zc:throwingNew`[`-`]  
  
## <a name="remarks"></a>备注  
  
因为 ISO C + + 98，标准已指定，默认值[运算符 new](../../standard-library/new-operators.md#op_new)引发`std::bad_alloc`内存分配失败时。 将返回 null 指针到 Visual Studio 6.0 的 Visual c + + 的版本上分配失败。 从 Visual Studio 2002，开始`operator new`符合标准和失败时引发。 若要支持使用较旧的分配形式的代码，Visual Studio 提供的可链接实现`operator new`中*nothrownew.obj* ，失败返回一个 null 指针。 默认情况下，编译器还生成防御性 null 检查，以防止这些较旧样式的分配器失败导致程序即时崩溃。 `/Zc:throwingNew`选项告知编译器省略这些 null 检查，假定所有链接内存分配器符合标准。 这不适用于显式非引发`operator new`重载，使用其他参数的类型声明`std::nothrow_t`和具有显式`noexcept`规范。  
  
从概念上讲，若要在自由储存中创建一个对象，编译器生成代码以分配其内存，然后调用其构造函数初始化内存。 因为 Visual c + + 编译器通常无法告知是否此代码将链接到一个不符合要求，非引发的分配器，默认情况下它还生成 null 检查，然后再调用的构造函数。 这可以防止 null 指针取消引用的构造函数调用中，如果非引发分配失败。 在大多数情况下，这些检查是必需的因为默认值`operator new`分配器引发而不是返回 null 指针。 检查还有不幸的副作用。 它们膨胀代码大小、 它们充满分支的预测指标，从而它们避免降低如 devirtualization 或初始化的对象的 const 传播其他有用的编译器优化。 检查存在仅对链接到的支持代码*nothrownew.obj*或具有自定义不符合要求`operator new`实现。 如果不使用不符合要求`operator new`，我们建议你使用`/Zc:throwingNew`来优化你的代码。  
  
如果你通过使用链接时间代码生成 (LTCG) 编译，不需要指定`/Zc:throwingNew`。 如果通过使用 LTCG 编译你的代码后，编译器可以检测到默认情况下，符合`operator new`使用实现。 如果是这样，编译器遗漏 null 检查自动。 链接器查找`/ThrowingNew`标志来告诉如果的实现`operator new`为一致性。 你可以通过在你自定义运算符的新实现的源中包含此指令指定到链接器此标志：  
  
```cpp  
#pragma comment(linker, "/ThrowingNew")  
```  
  
有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。  
  
## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
2.  从**配置**下拉列表菜单中，选择**所有配置**。  
3.  选择**配置属性**， **C/c + +**，**命令行**属性页。  
4.  修改**其他选项**属性以包含`/Zc:throwingNew`或`/Zc:throwingNew-`，然后选择**确定**。  
  
## <a name="see-also"></a>请参阅  
[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
[/Zc（一致性）](../../build/reference/zc-conformance.md)  
[noexcept (C++)](../../cpp/noexcept-cpp.md)  
[异常规范 (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)  
[终止 （异常）](../../standard-library/exception-functions.md#terminate)  
