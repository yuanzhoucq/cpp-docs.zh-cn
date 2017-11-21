---
title: ".Obj 文件作为链接器输入 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.assetid: 3028e423-8b10-4972-8eb4-6e9ae58f0a26
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ca8346f9ff29d097450eda4d8bfbfee7f7a3f522
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="obj-files-as-linker-input"></a>用作链接器输入的 .Obj 文件
链接器工具 （链接。EXE) 接受在通用对象文件格式 (COFF) 的.obj 文件。  
  
## <a name="remarks"></a>备注  
 Microsoft 提供了可下载的文档，用于定义通用对象文件格式。 有关详细信息，下载 8.1 或更高版本的修订[Microsoft 可移植可执行文件和通用对象文件格式规格的](http://go.microsoft.com/fwlink/?LinkId=93292)。  
  
## <a name="unicode-support"></a>Unicode 支持  
 Microsoft Visual c + + 编译器从 Visual Studio 2005 开始，支持 ISO/IEC C 和 c + + 标准定义的标识符中的 Unicode 字符。 以前版本的编译器支持在标识符中仅包含 ASCII 字符。 若要支持 Unicode 支持的函数、 类和静态对象的名称中，编译器和链接器，请使用 COFF 符号.obj 文件中的 Unicode utf-8 编码。 Utf-8 编码是与使用 Visual Studio 的早期版本的 ASCII 编码上级兼容。  
  
 有关编译器和链接器的详细信息，请参阅[编译器和链接器中的 Unicode 支持](../../build/reference/unicode-support-in-the-compiler-and-linker.md)。 有关 Unicode 标准的详细信息，请参阅[Unicode](http://go.microsoft.com/fwlink/?LinkId=37123)组织。  
  
## <a name="see-also"></a>另请参阅  
 [LINK 输入的文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [有关 Unicode 的支持](../../text/support-for-unicode.md)   
 [编译器和链接器中的 Unicode 支持](../../build/reference/unicode-support-in-the-compiler-and-linker.md)   
 [Unicode 标准](http://go.microsoft.com/fwlink/?LinkId=37123)   
 [通用对象文件格式规范](http://go.microsoft.com/fwlink/?LinkId=93292)