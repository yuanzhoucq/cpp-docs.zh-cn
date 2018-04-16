---
title: "链接器工具错误 LNK1107 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1107
dev_langs:
- C++
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fae412de31163aa1b5248af43227042cd04563ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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