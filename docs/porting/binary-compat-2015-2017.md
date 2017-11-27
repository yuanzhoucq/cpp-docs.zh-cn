---
title: "Visual Studio 2015 和 Visual Studio 2017 之间的 C++ 二进制兼容性 | Microsoft Docs"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 89bb772976050c8ebf0b7745aa0541c2de3e2fed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Visual Studio 2015 和 Visual Studio 2017 之间的 C++ 二进制兼容性


在 Visual Studio 以前的版本中，不能保证使用不同编译器工具集和运行时库生成的对象文件 (OBJ)、静态库 (LIB)、动态库 (DLL) 和可执行文件 (EXE) 之间的二进制兼容性。 这在 Visual Studio 2017 中发生了改变。 在 Visual Studio 2015 和 Visual Studio 2017 中，C++ 工具集的主版本号是 14（Visual Studio 2015 是 v140，Visual Studio 2017 是 v141）。 这反映了这样的事实：使用这两个版本之一的编译器编译的运行时库和应用程序在大多数情况下都是二进制兼容的。 这意味着，比如可以在 Visual Studio 2017 中创建 DLL，然后从用 Visual Studio 2015 编译的应用程序使用它，或者通过使用 2015 工具集生成的应用程序使用 Visual Studio 2017 可再发行库。  

以下为此规则的两种例外情况。 在以下情况中不能保证二进制兼容性：  

1) 静态库或对象文件是使用 /GL 编译器开关编译的。  

2) 应用程序使用版本号低于用于编译应用程序的工具集的版本号的可再发行库时。 换句话说，如果使用平台工具集 v141 来编译程序，则应用程序使用的任何可再发行库必须使用 v141 或更高版本编译。  

## <a name="see-also"></a>另请参阅  

[Visual C++ 更改历史记录](..\porting\visual-cpp-change-history-2003-2015.md)


