---
title: Compiler-Controlled LINK Options
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: bc7a6cc596f138daa373042abca51642c24cf737
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822322"
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options

CL 编译器会自动调用链接，除非指定了 /c 选项。 CL 提供了通过命令行选项和参数链接器的某些控制。 下表总结了 CL 影响链接的功能。

|CL 规范|CL 操作会影响链接|
|----------------------|---------------------------------|
|.C、.cxx、.cpp 或.def 以外任何文件扩展名|将文件名传递作为输入链接|
|*filename*.def|将传递 /DEF:*文件名*.def|
|/F*number*|传递 /STACK:*数*|
|/Fd*filename*|将传递 /PDB:*文件名*|
|/Fe*filename*|将传递 /out:*文件名*|
|/Fm*filename*|传递 /MAP:*文件名*|
|/Gy|创建封装的函数 (Comdat);启用函数级链接|
|/LD|将传递 /DLL|
|/LDd|将传递 /DLL|
|/link|将命令行的其余部分传递到链接|
|/MD 或 /MT|将默认库名放入.obj 文件|
|/Mdd 或 /MTd|将默认库名称放置在.obj 文件中。 定义符号 **_DEBUG**|
|/nologo|将传递 /NOLOGO|
|/Zd|传递 /DEBUG|
|/Zi 或/z7 标识|传递 /DEBUG|
|/Zl|省略.obj 文件中的默认库名称|

有关详细信息，请参阅[MSVC 编译器选项](compiler-options.md)。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
