---
title: "调用脚本 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StringRegister
dev_langs: C++
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cbf969f601bd90e84bf0ee15ae2ea3dcb392610
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="invoking-scripts"></a>调用脚本
[使用可替换参数 （注册机构的预处理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)讨论替换地图并提及的注册机构方法**AddReplacement**。 下表中描述了所有和注册机构有八个特定于编写脚本，其他方法。  
  
|方法|语法/说明|  
|------------|-------------------------|  
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **，UINT** `nID` **，LPCOLESTR** `szType` **);** <br /><br /> 注册模块的资源中包含的脚本。 *resFileName*指示模块本身的 UNC 路径。 `nID`和`szType`分别包含资源的 ID 和类型。|  
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **，UINT** `nID` **，LPCOLESTR** `szType` **);** <br /><br /> 注销模块的资源中包含的脚本。 *resFileName*指示模块本身的 UNC 路径。 `nID`和`szType`分别包含资源的 ID 和类型。|  
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **，LPCOLESTR***szID* **，LPCOLESTR** `szType` **);** <br /><br /> 注册模块的资源中包含的脚本。 *resFileName*指示模块本身的 UNC 路径。 *szID*和`szType`分别包含资源的字符串标识符和类型。|  
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **，LPCOLESTR***szID* **，LPCOLESTR** `szType` **);** <br /><br /> 注销模块的资源中包含的脚本。 *resFileName*指示模块本身的 UNC 路径。 *szID*和`szType`分别包含资源的字符串标识符和类型。|  
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***fileName***);** <br /><br /> 在文件中注册的脚本。 *fileName*是包含 （或） 资源脚本的文件的 UNC 路径。|  
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***fileName***);** <br /><br /> 注销一个文件中的脚本。 *fileName*是包含 （或） 资源脚本的文件的 UNC 路径。|  
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***数据***);** <br /><br /> 在字符串中注册的脚本。 *数据*包含脚本本身。|  
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***数据***);** <br /><br /> 注销一个字符串中的脚本。 *数据*包含脚本本身。|  
  
 **ResourceRegisterSz**和**ResourceUnregisterSz**，类似于**ResourceRegister**和**ResourceUnregister**，但允许你指定字符串标识符。  
  
 方法**FileRegister**和**FileUnregister**非常有用，如果您不希望资源中的脚本，或如果您希望其自己的文件中的脚本。 方法**StringRegister**和**StringUnregister**允许.rgs 文件存储在动态分配的字符串。  
  
## <a name="see-also"></a>请参阅  
 [创建注册器脚本](../atl/creating-registrar-scripts.md)

