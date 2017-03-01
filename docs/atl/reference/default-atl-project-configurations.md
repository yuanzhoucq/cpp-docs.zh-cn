---
title: "默认 ATL 项目配置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, default configurations
ms.assetid: 7e272722-41af-4330-b965-a6d74ec16880
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 41ab65c411bef478d063e5165d3167f58ace37d7
ms.lasthandoff: 02/24/2017

---
# <a name="default-atl-project-configurations"></a>默认 ATL 项目配置
本主题将在 Visual c + + 6.0 的默认项目配置 Visual c + +.NET 中的默认 ATL 项目配置进行比较。  
  
## <a name="visual-c-net-default-configurations"></a>Visual c + +.NET 的默认配置  
 在 Visual c + +.NET 中，ATL 项目向导默认情况下创建两个项目配置。  
  
### <a name="visual-c-net-configurations"></a>Visual c + +.NET 配置  
  
|配置|字符集|ATL 的使用|  
|-------------------|-------------------|----------------|  
|发布|MBCS|DLL|  
|调试|MBCS|DLL|  
  
 **字符集**， **ATL 使用**和均可进行修改以**项目设置**下的对话框**常规**选项卡。 此外可以添加您自己的配置使用配置管理器。 有关详细信息，请参阅[Build 配置中](/visualstudio/ide/understanding-build-configurations)。  
  
## <a name="version-60-default-configurations"></a>版本 6.0 的默认配置  
 在 Visual c + + 6.0 版，ATL COM AppWizard （现在称为 ATL 项目向导） 默认情况下创建六个项目配置。 配置已发布、 调试、 Unicode 和 CRT 和 ATL 设置使用的变动。 如果需要的话，可以在 Visual c + +.NET 中使用配置管理器中，复制所有这些配置。  
  
### <a name="version-60-configurations"></a>6.0 版配置  
  
|配置|字符集|ATL 的使用|  
|-------------------|-------------------|----------------|  
|调试|MBCS|Static|  
|调试 Unicode|UNICODE|Static|  
|释放最小依赖关系|MBCS|Static|  
|释放最小依赖关系 Unicode|UNICODE|Static|  
|释放最小大小|MBCS|DLL|  
|释放最小大小 Unicode|UNICODE|DLL|  
  
## <a name="see-also"></a>另请参阅  
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [配置管理器对话框中](http://msdn.microsoft.com/en-us/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [编译和生成](/visualstudio/ide/compiling-and-building-in-visual-studio)


