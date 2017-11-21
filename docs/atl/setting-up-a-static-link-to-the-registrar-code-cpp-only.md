---
title: "设置注册机构代码 （c + +） 的静态链接 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b8eb77bc6f99ab6b7d8ca9d51f1a7a8549d8f0c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>设置注册机构代码 （c + +） 的静态链接
C + + 客户端可以创建指向注册机构的代码的静态链接。 静态链接的注册机构的分析器将大约 5 K 添加到发布版本。  
  
 设置静态链接的最简单方法假定你已指定[DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid)对象的声明中。 （这是使用 ATL 的默认规范）  
  
### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>若要创建使用 DECLARE_REGISTRY_RESOURCEID 的静态链接  
  
1.  指定[/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY`而不是 /D**_ATL_DLL**。  
  
2.  重新编译。  
  
## <a name="see-also"></a>另请参阅  
 [注册表组件 （注册器）](../atl/atl-registry-component-registrar.md)

