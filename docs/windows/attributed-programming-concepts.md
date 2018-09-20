---
title: 特性化编程概念 |Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributed programming [C++]
- attributes [C++/CLI]
- programming [C++], attributed programming
ms.assetid: 563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: abe76a4153ecfb0e4db4ce9e92eb63f5b00067ff
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394642"
---
# <a name="attributed-programming-concepts"></a>特性化编程概念

Visual c + + 包含多种材料，帮助您在程序中使用属性。 属性，Visual c + + 中的新功能旨在简化 COM 编程和.NET Framework 公共语言运行时开发。 当在源文件中包含的属性时，编译器可使用提供程序动态链接库 (DLL)，用于插入代码或修改生成的对象文件中的代码。 有帮助的.idl 文件、 接口、 类型库和其他 COM 元素创建的属性。 在集成的开发环境 (IDE) 中，通过这些向导和属性窗口支持属性。

虽然属性消除一些详细编写 COM 对象所需的编码，您需要在后台[COM 基础知识](/windows/desktop/com/the-component-object-model)以最佳方式使用它们。

## <a name="in-this-section"></a>本节内容

[特性用途](../windows/purpose-of-attributes.md)<br/>
提供特性化编程的概述。

[特性的基本机制](../windows/basic-mechanics-of-attributes.md)<br/>
介绍属性在项目中的工作方式。

[生成特性化程序](../windows/building-an-attributed-program.md)<br/>
提供有关在项目中使用 c + + 编译器选项的信息。

[特性类别](../windows/attribute-categories.md)<br/>
提供指向 Visual c + + 中使用的属性的类别。

[属性 Programmming 常见问题](../windows/attribute-programming-faq.md)<br/>
解答有关常见问题特性化编程。

## <a name="related-sections"></a>相关章节

[属性参考](../windows/cpp-attributes-reference.md)<br/>
提供指向参考主题描述各个属性和它们的使用。

[调试插入的代码](/visualstudio/debugger/how-to-debug-injected-code)<br/>
描述调试特性化的程序。

[__super](../cpp/super.md)和[__interface](../cpp/interface.md)  
与特性化编程相关的新 c + + 关键字的链接。