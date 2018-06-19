---
title: -ALLOWISOLATION （清单查找） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0e063aa51e136dfcc7a4445948e8a68d7a99bca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369833"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION（清单查找）
指定清单查找的行为。  
  
## <a name="syntax"></a>语法  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>备注  
 **/ALLOWISOLATION:NO**指示像没有清单，将会加载的 Dll 和导致链接器设置`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`optional 标头中位`DllCharacteristics`字段。  
  
 **/ALLOWISOLATION**会导致操作系统进行清单查找和加载。  
  
 **/ALLOWISOLATION**是默认设置。  
  
 当可执行文件禁用隔离时，Windows 加载程序不会尝试查找新创建的进程的应用程序清单。 新的进程将具有默认激活上下文，即使在可执行文件或放置在名称的可执行文件所在的目录清单 * 可执行文件的名称 ***。 exe.manifest**。  
  
 有关详细信息，请参阅[清单文件引用](http://msdn.microsoft.com/library/aa375632)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**清单文件**属性页。  
  
5.  修改**允许隔离**属性。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)