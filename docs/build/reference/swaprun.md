---
title: "-SWAPRUN |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /swaprun
dev_langs: C++
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 249ed999d9a60116875e88553863ef5cd234ade9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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