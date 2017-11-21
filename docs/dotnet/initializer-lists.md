---
title: "初始值设定项列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99d62f1aec8cf06fff5de98f4681ddc67c3a9e71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="initializer-lists"></a>初始值设定项列表
在构造函数中的初始值设定项列表现在称为先于基类构造函数中。  
  
## <a name="remarks"></a>备注  
 在 Visual c + + 2005 中之前, 的基类构造函数时，调用在初始值设定项列表之前使用 Managed Extensions for c + + 编译。 现在，使用编译时**/clr**，都会首先调用初始值设定项列表。  
  
## <a name="see-also"></a>另请参阅  
 [常规语言更改 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)