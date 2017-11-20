---
title: "生成特性化的程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tlb files
- MIDL
- MIDL, linker output
- IDL files
- tlb files, building attributed programs
- .tlb files, building attributed programs
- IDL files, building
- attributes [C++], building type libraries and .idl files
- .tlb files
- .idl files, building
- type libraries, linker options for building
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a757cbbb7bb9e080a9492ecabfd0542714cf2c7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="building-an-attributed-program"></a>生成特性化程序
Visual c + + 特性置于你的源代码后，您可能希望 Visual c + + 编译器可为你生成类型库和.idl 文件。 以下链接器选项生成.tlb 和.idl 文件的帮助：  
  
-   [/IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 某些项目包含多个独立的.idl 文件。 这些凭据用于进行生成两个或多个.tlb 文件并根据需要将它们绑定到的资源块。 在 Visual c + + 中，当前不支持此方案。  
  
 此外，Visual c + + 链接器将输出所有 IDL 相关属性信息添加到单个 MIDL 文件。 将无法从单个项目中生成两个类型库。  
  
## <a name="see-also"></a>另请参阅  
 [概念](../windows/attributed-programming-concepts.md)