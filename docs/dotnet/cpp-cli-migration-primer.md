---
title: "C + + /cli 迁移入门 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5861a4931a1241a213157b94ca189c6b95f0fb6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ccli-migration-primer"></a>C++/CLI 迁移入门
这是你的 Visual c + + 程序将从移动 Managed Extensions for c + + 到 Visual c + + 的指南。 有关语法的更改的清单摘要，请参阅[(NOTINBUILD) c + + 语法升级清单的托管扩展](http://msdn.microsoft.com/en-us/edbded88-7ef3-4757-bd9d-b8f48ac2aada)。  
  
 C + + /cli CLI 扩展到 ISO c + + 标准语言动态组件编程范例。 新语言提供大量的重大改进，通过托管扩展。 本部分提供对 Visual c + + 这样的映射存在，其中指出存在没有映射这些构造 c + + 语言功能的托管扩展的枚举的列表以及它们的映射。  
  
## <a name="in-this-section"></a>本节内容  
 [更改概要 (C++/CLI)](../dotnet/outline-of-changes-cpp-cli.md)  
 快速参考，提供所做的更改的列表在五个常规类别高级大纲。  
  
 [语言关键字 (C++/CLI)](../dotnet/language-keywords-cpp-cli.md)  
 讨论语言关键字，其中包括双下划线删除以及上下文和空格分隔的关键字的介绍中的更改。  
  
 [托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)  
 查看中声明的公共类型系统 (CTS) 的语法更改这包括类、 数组 （包括参数数组）、 枚举和等等的声明中的更改。  
  
 [类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)  
 显示涉及如标量属性、 索引属性、 运算符、 委托和事件的类成员的更改。  
  
 [值类型及其行为 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 重点值类型和新的内部和钉住指针系列。 它还介绍了大量的重大语义的更改，例如隐式装箱、 永久性装箱的值类型和值类中的默认构造函数的支持删除简介。  
  
 [常规语言更改 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)  
 语义的详细信息更改，例如强制转换表示法的支持字符串文本的行为和更改语义之间 ISO c + + 和 C + + /cli CLI。  
  
## <a name="see-also"></a>另请参阅  
 [混合 （本机和托管） 程序集](../dotnet/mixed-native-and-managed-assemblies.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)