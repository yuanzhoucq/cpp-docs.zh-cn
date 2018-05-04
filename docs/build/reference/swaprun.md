---
title: -SWAPRUN |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /swaprun
dev_langs:
- C++
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6e8af5b23d2e6cd0759f75c4054e0a811f687e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="swaprun"></a>/SWAPRUN
```  
/SWAPRUN:{[!]NET|[!]CD}  
```  
  
## <a name="remarks"></a>备注  
 此选项编辑映像以告知操作系统的映像复制到一个交换文件，并从该处运行它。 将此选项用于驻留在网络或可移动媒体的映像。  
  
 你可以添加或删除的 NET 或 CD 限定符：  
  
-   NET 指示图像驻留在网络上。  
  
-   CD 指示图像驻留在 CD-ROM 或类似的可移动媒体。  
  
-   使用 ！ NET 和 ！要反转的 NET 和 CD 的效果的 CD。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)