---
title: 如何： 生成独立的应用程序使用 COM 组件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed2f43721eb698552ccde3e1b51ed4d6e467179
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>如何：生成独立应用程序以使用 COM 组件
独立应用程序是具有内置在程序的清单的应用程序。 你可以创建独立的应用程序使用 COM 组件。  
  
### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>COM 将引用添加到独立的应用程序清单  
  
1.  打开独立的应用程序的项目属性页。  
  
2.  展开**配置属性**节点，然后展开**清单工具**节点。  
  
3.  选择**独立 COM**属性页，然后将设置**组件文件名称**属性设置为你想要使用的独立应用程序的 COM 组件的名称。  
  
4.  单击 **“确定”**。  
  
### <a name="to-build-manifests-into-isolated-applications"></a>要生成为独立应用程序的清单  
  
1.  打开独立的应用程序的项目属性页。  
  
2.  展开**配置属性**节点，然后展开**清单工具**节点。  
  
3.  选择**输入和输出**属性页，然后将设置**嵌入清单**属性等于**是**。  
  
4.  单击 **“确定”**。  
  
5.  生成解决方案。  
  
## <a name="see-also"></a>请参阅  
 [独立应用程序](http://msdn.microsoft.com/library/aa375190)   
 [有关通过并行程序集](http://msdn.microsoft.com/library/ff951640)