---
title: Visual Studio 2015 和 Visual Studio 2017 之间的 C++ 二进制兼容性 | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcd315631d74c652177dba99cbe533ad91f68474
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Visual Studio 2015 和 Visual Studio 2017 之间的 C++ 二进制兼容性


在 Visual Studio 以前的版本中，不能保证使用不同编译器工具集和运行时库生成的对象文件 (OBJ)、静态库 (LIB)、动态库 (DLL) 和可执行文件 (EXE) 之间的二进制兼容性。 这在 Visual Studio 2017 中发生了改变。 在 Visual Studio 2015 和 Visual Studio 2017 中，C++ 工具集的主版本号是 14（Visual Studio 2015 是 v140，Visual Studio 2017 是 v141）。 这反映了这样的事实：使用这两个版本之一的编译器编译的运行时库和应用程序在大多数情况下都是二进制兼容的。 这意味着，比如可以在 Visual Studio 2017 中创建 DLL，然后从用 Visual Studio 2015 编译的应用程序使用它，或者通过使用 2015 工具集生成的应用程序使用 Visual Studio 2017 可再发行库。  

以下为此规则的两种例外情况。 在以下情况中不能保证二进制兼容性：  

1) 静态库或对象文件是使用 /GL 编译器开关编译的。  

2) 构建当前使用的库时所用的工具集的版本高于编译和链接应用程序时使用的工具集。 例如，通过工具集 19.12 编译和链接的程序可以使用通过工具集 19.0 到 19.12 编译的库。 不支持将 19.x 程序与使用 Visual Studio 2013 或更早版本生成的库进行链接。


## <a name="see-also"></a>请参阅  

[Visual C++ 更改历史记录](..\porting\visual-cpp-change-history-2003-2015.md)


