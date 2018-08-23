---
title: 初始值设定项列表 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6634b749480e5108548de0c8b53f8b09cc5a42c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127947"
---
# <a name="initializer-lists"></a>初始值设定项列表
在构造函数中的初始值设定项列表现在称为先于基类构造函数中。  
  
## <a name="remarks"></a>备注  
 在 Visual c + + 2005 中之前, 的基类构造函数时，调用在初始值设定项列表之前使用 Managed Extensions for c + + 编译。 现在，使用编译时 **/clr**，都会首先调用初始值设定项列表。  
  
## <a name="see-also"></a>请参阅  
 [常规语言更改 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)