---
title: 生成特性化的程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7909884a355ccad5e1bf9d18a38dd3e4690296ee
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42587502"
---
# <a name="building-an-attributed-program"></a>生成特性化程序

Visual c + + 特性置于源代码后，你可能想 Visual c + + 编译器为您生成类型库和.idl 文件。 以下链接器选项可帮助您生成.tlb 和.idl 文件：

- [/IDLOUT](../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)

某些项目包含多个独立的.idl 文件。 这些用于生成两个或多个.tlb 文件并根据需要将其绑定到的资源块。 在 Visual c + + 中，当前不支持此方案。

此外，Visual c + + 链接器将输出到单个 MIDL 文件的所有与 IDL 相关的属性信息。 将没有办法从单个项目生成两个类型库。

## <a name="see-also"></a>请参阅

[概念](../windows/attributed-programming-concepts.md)