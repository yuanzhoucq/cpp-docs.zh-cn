---
title: C + + /cli 迁移入门 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88b32ea226971c0fa5b6d269a8992629c3c4de77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385426"
---
# <a name="ccli-migration-primer"></a>C++/CLI 迁移入门

这是您的 Visual c + + 程序从转为托管扩展 c + + 的 Visual c + + 的指南。

C + + /cli CLI 扩展到 ISO-C + + 标准语言动态组件编程范例。 新的语言通过托管扩展提供了大量重要改进。 本部分提供对 c + + 语言功能的托管扩展的枚举的列表以及它们映射到 Visual c + + 这样的映射存在，其中指出存在没有映射这些构造。

## <a name="in-this-section"></a>本节内容

[更改概要 (C++/CLI)](../dotnet/outline-of-changes-cpp-cli.md)<br/>
方便参考，提供的更改的列表下有五个常规类别的高度概括。

[语言关键字 (C++/CLI)](../dotnet/language-keywords-cpp-cli.md)<br/>
讨论语言关键字，包括删除双下划线和的上下文和空格分隔的关键字引入的更改。

[将托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
查看在声明中的通用类型系统 (CTS) 的语法更改这包括类、 数组 （包括参数数组）、 枚举和等等的声明中的更改。

[类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
显示涉及类成员，例如标量属性、 索引属性、 运算符、 委托和事件的更改。

[值类型及其行为 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
重点讨论值类型和内部指针和钉住指针的新系列。 它还讨论若干重大语义更改，如隐式装箱，装箱的值类型的不可变性和对值类内部的默认构造函数的支持删除引入。

[常规语言更改 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
详细信息如支持强制转换表示法的语义更改字符串文本的行为和 ISO c + + 和 C + 之间的语义更改 + CLI。

## <a name="see-also"></a>请参阅

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)