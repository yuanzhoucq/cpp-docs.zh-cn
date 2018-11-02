---
title: 调用脚本 (ATL)
ms.date: 11/04/2016
f1_keywords:
- StringRegister
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
ms.openlocfilehash: 170eb4c29571fcec8797727f54630894c9198442
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650549"
---
# <a name="invoking-scripts"></a>调用脚本

[使用可替换参数 （注册机构的预处理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)讨论替换映射，并提到注册机构方法**AddReplacement**。 注册机构都有八个特定于脚本编写，其他方法，并在下表介绍了所有。

|方法|语法/说明|
|------------|-------------------------|
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **，UINT** `nID` **，LPCOLESTR** `szType` **);**<br /><br /> 注册模块的资源中包含的脚本。 *resFileName*指示对模块自身的 UNC 路径。 *nID*并*szType*分别包含资源的 ID 和类型。|
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **，UINT** `nID` **，LPCOLESTR** `szType` **);**<br /><br /> 注销模块的资源中包含的脚本。 *resFileName*指示对模块自身的 UNC 路径。 *nID*并*szType*分别包含资源的 ID 和类型。|
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **，LPCOLESTR***szID* **，LPCOLESTR** `szType`**);**<br /><br /> 注册模块的资源中包含的脚本。 *resFileName*指示对模块自身的 UNC 路径。 *szID*并*szType*分别包含资源的字符串标识符和类型。|
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **，LPCOLESTR***szID* **，LPCOLESTR** `szType` **);**<br /><br /> 注销模块的资源中包含的脚本。 *resFileName*指示对模块自身的 UNC 路径。 *szID*并*szType*分别包含资源的字符串标识符和类型。|
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***文件名***);**<br /><br /> 在文件中注册的脚本。 *文件名*是包含 （或） 资源脚本文件的 UNC 路径。|
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***文件名***);**<br /><br /> 取消注册文件中的脚本。 *文件名*是包含 （或） 资源脚本文件的 UNC 路径。|
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***数据***);**<br /><br /> 在字符串中注册的脚本。 *数据*包含脚本本身。|
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***数据***);**<br /><br /> 注销在字符串中的脚本。 *数据*包含脚本本身。|

**ResourceRegisterSz**并**ResourceUnregisterSz**，类似于**ResourceRegister**并**ResourceUnregister**，但允许你指定一个字符串，标识符。

方法**FileRegister**并**FileUnregister**如果不希望在资源中的脚本，或者如果你想在其自己的文件中的脚本将非常有用。 方法**StringRegister**并**StringUnregister**允许 rgs 文件存储在动态分配的字符串。

## <a name="see-also"></a>请参阅

[创建注册器脚本](../atl/creating-registrar-scripts.md)

