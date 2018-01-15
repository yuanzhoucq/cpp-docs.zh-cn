---
title: "如何： 生成免注册 COM 组件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 018a3ba707f4c5cff73b5a5c54f82400a79a8d46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-build-registration-free-com-components"></a>如何：生成免注册 COM 组件
免注册 COM 组件是具有内置于 Dll 的清单的 COM 组件。  
  
### <a name="to-build-manifests-into-com-components"></a>清单内置于 COM 组件  
  
1.  打开 COM 组件的项目属性页。  
  
2.  展开**配置属性**节点，然后展开**清单工具**节点。  
  
3.  选择**输入和输出**属性页，然后将设置**嵌入清单**属性等于**是**。  
  
4.  单击 **“确定”**。  
  
5.  生成解决方案。  
  
## <a name="see-also"></a>请参阅  
 [独立应用程序](http://msdn.microsoft.com/library/aa375190)   
 [有关通过并行程序集](http://msdn.microsoft.com/library/ff951640)   
 [如何：生成独立应用程序以使用 COM 组件](../build/how-to-build-isolated-applications-to-consume-com-components.md)