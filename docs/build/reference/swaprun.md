---
title: /SWAPRUN
ms.date: 11/04/2016
f1_keywords:
- /swaprun_editbin
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
ms.openlocfilehash: 83aa2cdb445ed1ac6bac5b1237f90a116986b0a9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438854"
---
# <a name="swaprun"></a>/SWAPRUN

```
/SWAPRUN:{[!]NET|[!]CD}
```

## <a name="remarks"></a>备注

此选项可编辑图像，告知操作系统将映像复制到交换文件，然后从该文件运行。 对于位于网络或可移动媒体上的映像，请使用此选项。

可以添加或删除 NET 或 CD 限定符：

- NET 指示映像驻留在网络上。

- CD 指示映像驻留在 cd-rom 或类似可移动介质上。

- 使用！ NET 和！CD 来反转网络和 CD 的效果。

## <a name="see-also"></a>另请参阅

[EDITBIN 选项](editbin-options.md)
