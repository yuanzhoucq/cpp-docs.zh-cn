---
title: 链接器工具警告 LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 0abad1b98ff4782f077312752603ec17fd611c12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527330"
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