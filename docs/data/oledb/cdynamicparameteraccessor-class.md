---
title: CDynamicParameterAccessor 类 |Microsoft 文档
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicParameterAccessor class
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b9478a5b2cc2190219ce2b297d1908683577c9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor 类

类似于[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)但获取参数信息，以通过调用设置[ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters)接口。

## <a name="syntax"></a>语法

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-cdynamicparameteraccessor.md)|构造函数。|
|[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)|从缓冲区中检索参数数据。|
|[GetParamCount](../../data/oledb/cdynamicparameteraccessor-getparamcount.md)|检索访问器中的参数数目。|
|[GetParamIO](../../data/oledb/cdynamicparameteraccessor-getparamio.md)|确定指定参数是输入参数还是输出参数。|
|[GetParamLength](../../data/oledb/cdynamicparameteraccessor-getparamlength.md)|检索存储在缓冲区中的指定参数的长度。|
|[GetParamName](../../data/oledb/cdynamicparameteraccessor-getparamname.md)|检索指定参数的名称。|
|[GetParamStatus](../../data/oledb/cdynamicparameteraccessor-getparamstatus.md)|检索存储在缓冲区中的指定参数的状态。|
|[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)|检索存储在缓冲区中的指定参数的字符串数据。|
|[GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)|检索指定参数的数据类型。|
|[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)|使用参数数据设置缓冲区。|
|[SetParamLength](../../data/oledb/cdynamicparameteraccessor-setparamlength.md)|设置存储在缓冲区中的指定参数的长度。|
|[SetParamStatus](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|设置存储在缓冲区中的指定参数的状态。|
|[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|设置存储在缓冲区中的指定参数的字符串数据。|

## <a name="remarks"></a>备注

访问接口必须支持 `ICommandWithParameters` 以便使用者使用此类。

参数信息存储在由此类创建和管理的缓冲区中。 通过使用 [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 和 [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)从缓冲区中获取参数数据。

有关演示如何使用此类来执行 SQL Server 存储过程并获取输出参数值的示例，请参阅[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)示例中的代码[Microsoft VCSamples](https://github.com/Microsoft/VCSamples)在 GitHub 上的存储库。

## <a name="requirements"></a>要求

**标头**：atldbcli.h

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)  
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)  
[CAccessor 类](../../data/oledb/caccessor-class.md)  
[CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)  
[CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)  
