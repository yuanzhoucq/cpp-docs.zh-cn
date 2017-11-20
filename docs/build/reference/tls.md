---
title: "-TLS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /TLS
dev_langs: C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da65c67a38d9517ed2671fcea69a583b9ba65d6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="tls"></a>/TLS
显示从可执行文件的 IMAGE_TLS_DIRECTORY 结构。  
  
## <a name="remarks"></a>备注  
 / TLS 显示 TLS 结构的字段以及 TLS 回调函数的地址。  
  
 如果程序不使用线程本地存储区，其映像将不包含 TLS 结构。  请参阅[线程](../../cpp/thread.md)有关详细信息。  
  
 IMAGE_TLS_DIRECTORY 在 winnt.h 中定义。  
  
## <a name="see-also"></a>另请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)