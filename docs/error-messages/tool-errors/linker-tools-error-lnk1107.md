---
title: 链接器工具错误 LNK1107 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1107
dev_langs:
- C++
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fee2105cb0c12287cd2b47636f0e47011854a608
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1107"></a>链接器工具错误 LNK1107
无效或已损坏的文件： 无法读取位置  
  
 该工具无法读取文件。 重新创建该文件。  
  
 如果您试图将传递一个模块，也可能发生 LNK1107 (使用创建的.dll 或.netmodule 扩展名[/clr:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md)或[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)) 到链接器; 改为传递.obj 文件。  
  
 如果编译下面的示例：  
  
```  
// LNK1107.cpp  
// compile with: /clr /LD  
public ref class MyClass {  
public:  
   void Test(){}  
};  
```  
  
 然后指定**链接 LNK1107.dll**在命令行中，你将获取 LNK1107。  若要解决此错误，请指定**链接 LNK1107.obj**相反。