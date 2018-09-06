---
title: 链接器工具警告 LNK4197 |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4197
dev_langs:
- C++
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55044ce511e2584e2859b7e8a8d723cbe0976105
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894481"
---
# <a name="linker-tools-warning-lnk4197"></a>链接器工具警告 LNK4197

> 导出*exportname*多次; 使用第一个规范指定

在多个指定导出和不同的方式。 链接器使用的第一个规范而忽略其余部分。

如果您正在重新生成的 C 运行时库，可以忽略此消息。

如果导出多次指定完全相同的方式，链接器将不会发出警告。

例如，以下内容的.def 文件会导致此警告：

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 同一个导出指定命令行上 (通过导出:) 和.def 文件中。

2. 使用不同的属性在.def 文件中两次列出同一导出。