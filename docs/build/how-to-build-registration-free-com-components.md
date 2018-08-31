---
title: 如何： 生成免注册 COM 组件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1eaf9417f4d2b3b825933589556055772b84e057
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197408"
---
# <a name="how-to-build-registration-free-com-components"></a>如何：生成免注册 COM 组件
免注册 COM 组件是 COM 组件，具有内置 Dll 的清单。  
  
### <a name="to-build-manifests-into-com-components"></a>若要为 COM 组件生成清单  
  
1.  打开 COM 组件的项目属性页。  
  
2.  展开**配置属性**节点，然后展开**清单工具**节点。  
  
3.  选择**输入和输出**属性页，然后将设置**嵌入清单**属性等于**是**。  
  
4.  单击 **“确定”**。  
  
5.  生成解决方案。  
  
## <a name="see-also"></a>请参阅  
 [独立的应用程序](/windows/desktop/SbsCs/isolated-applications)   
 [有关通过并行程序集](/windows/desktop/SbsCs/about-side-by-side-assemblies-)   
 [如何：生成独立应用程序以使用 COM 组件](../build/how-to-build-isolated-applications-to-consume-com-components.md)