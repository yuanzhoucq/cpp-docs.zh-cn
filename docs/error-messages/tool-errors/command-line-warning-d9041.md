---
title: 命令行警告 D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 7c685a1ca3195ad4ab52bab8b5d32b1a51534b24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196570"
---
# <a name="command-line-warning-d9041"></a>命令行警告 D9041

"/option" 的值 "value" 无效;假定为 "value";指定此警告时将 "/analyze" 添加到命令行选项

代码分析警告编号已添加到 **/wd**、 **/we**、 **/wo**或 **/wl**命令行选项，而无需同时指定 **/analyze**命令行选项。 若要更正此错误，请添加 " **/analyze**命令行" 选项，或从相应的 " **/w** " 命令行选项中删除无效的警告编号。

## <a name="example"></a>示例

以下命令行示例生成警告 D9041：

```
cl /EHsc /LD /wd6001 filename.cpp
```

若要修复此警告，请添加 " **/analyze** " 命令行选项。 如果编译器的版本不支持 **/analyze** ，请从 **/wd**选项中删除无效的警告编号。

## <a name="see-also"></a>另请参阅

[命令行错误 D8000 - D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC 编译器选项](../../build/reference/compiler-options.md)
