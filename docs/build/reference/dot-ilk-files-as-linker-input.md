---
title: ".用作链接器输入的 ilk 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e7d801992beb75ccc14e185fc062dc4c51f8433
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ilk-files-as-linker-input"></a>用作链接器输入的 .Ilk 文件
链接时以增量方式，LINK 将更新其在第一个增量链接过程中创建的.ilk 状态文件。 此文件具有相同的基名称为.exe 文件或.dll 文件，并具有扩展.ilk。 在后续的增量链接期间链接更新.ilk 文件。 如果缺少.ilk 文件，则 LINK 执行完全链接和创建一个新的.ilk 文件。 如果.ilk 文件不可用，则 LINK 执行非增量链接。 有关增量链接的详细信息，请参阅[增量链接 (/incremental)](../../build/reference/incremental-link-incrementally.md)选项。  
  
## <a name="see-also"></a>另请参阅  
 [LINK 输入的文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)