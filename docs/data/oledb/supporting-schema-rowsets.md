---
title: "支持架构行集合 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 39b969349ee09e5882677b701030ef9c0792522a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="supporting-schema-rowsets"></a>支持架构行集
架构行集允许使用者无需知道其基础结构或架构中获取有关数据存储区的信息。 例如，数据存储区可能包含表组成用户定义的层次结构，因此将无法通过阅读确保除架构的知识的方式。 （作为另一个示例，请注意，Visual c + + 向导使用架构行集生成使用者的访问器。）若要允许使用者便可以执行此操作，提供程序的会话对象公开的方法上[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)接口。 在 Visual c + + 应用程序，你使用[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)类，以实现**IDBSchemaRowset**。  
  
 `IDBSchemaRowsetImpl` 支持以下方法：  
  
-   [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)检查针对架构行集的限制的有效性。  
  
-   [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)实现 COM 对象创建者函数由模板参数指定的对象。  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)指定在特定架构行集支持哪些限制。  
  
-   [Idbschemarowset::](../../data/oledb/idbschemarowsetimpl-getrowset.md)返回架构行集 （从接口继承）。  
  
-   [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)返回架构行集的列表可通过访问`IDBSchemaRowsetImpl::GetRowset`（从接口继承）。  
  
## <a name="atl-ole-db-provider-wizard-support"></a>ATL OLE DB 提供程序向导支持  
 ATL OLE DB 提供程序向导创建会话标头文件中的三个架构类：  
  
-   **C** *ShortName* **SessionTRSchemaRowset**  
  
-   **C** *ShortName* **SessionColSchemaRowset**  
  
-   **C** *ShortName* **SessionPTSchemaRowset**  
  
 这些类响应的使用者请求架构信息;请注意，OLE DB 规范需要支持这些三个架构行集：  
  
-   **C** *短名称* **SessionTRSchemaRowset**处理表信息的请求 (`DBSCHEMA_TABLES`架构行集)。  
  
-   **C** *短名称* **SessionColSchemaRowset**处理列信息的请求 ( **DBSCHEMA_COLUMNS**架构行集)。 向导提供了这些类，该类返回 DOS 提供程序的架构信息的示例实现。  
  
-   **C** *短名称* **SessionPTSchemaRowset**处理有关提供程序类型的架构信息的请求 ( **DBSCHEMA_PROVIDER_TYPES**架构行集）。 向导提供的默认实现返回`S_OK`。  
  
 你可以自定义这些类以处理适合于你的提供商的架构信息：  
  
-   在**C***短名称***SessionTRSchemaRowset**，必须填写目录、 表和描述字段 (**trData.m_szType**， **trData.m_szTable**，和**trData.m_szDesc**)。 该向导生成的示例使用只有一个行 （表）。 其他提供程序可能会返回多个表。  
  
-   在**C***短名称***SessionColSchemaRowset**，你将为表的名称传递给**DBID**。  
  
## <a name="setting-restrictions"></a>设置限制  
 架构行集支持中的一个重要概念设置限制，您执行此操作使用`SetRestrictions`。 限制允许使用者只提取匹配行（例如，查找表“MyTable”中的所有列）。 限制是可选的，如果不支持任何限制（默认设置），则始终返回所有数据。 有关支持限制的提供程序的示例，请参阅[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)示例。  
  
## <a name="setting-up-the-schema-map"></a>设置架构映射  
 设置在中 UpdatePV Session.h 诸如此类架构映射：  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 若要支持**IDBSchemaRowset**，你必须支持`DBSCHEMA_TABLES`， **DBSCHEMA_COLUMNS**，和**DBSCHEMA_PROVIDER_TYPES**。 你可以自行添加其他架构行集。  
  
 声明具有的架构行集类`Execute`如方法`CUpdateSessionTRSchemaRowset`UpdatePV 中：  
  
```  
class CUpdateSessionTRSchemaRowset :   
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,   
                              CTABLESRow, CUpdateSession >  
...  
// Execute looks like this; what pointers does the consumer use?  
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,   
                    ULONG cRestrictions, const VARIANT* rgRestrictions)  
```  
  
 请注意，`CUpdateSession`继承自`IDBSchemaRowsetImpl`，所以它可以处理的方法的所有限制。 使用`CSchemaRowsetImpl`，声明三个被子类 （在上面的架构映射中列出）： `CUpdateSessionTRSchemaRowset`， `CUpdateSessionColSchemaRowset`，和`CUpdateSessionPTSchemaRowset`。 每个这些子类别都有`Execute`处理其各自的一组限制 （搜索条件） 的方法。 每个`Execute`方法比较的值`cRestrictions`和`rgRestrictions`参数。 请参阅中的这些参数的说明[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)。  
  
 有关哪些限制对应于特定架构行集的详细信息，请查阅上的架构行集 Guid 表中[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程序员参考*中Windows SDK。  
  
 例如，如果你支持**TABLE_NAME**限制`DBSCHEMA_TABLES`，你将执行以下操作：  
  
 首先，查找`DBSCHEMA_TABLES`和发现该解决方案支持四个限制 （按顺序）。  
  
|架构行集限制|限制值|  
|-------------------------------|-----------------------|  
|**TABLE_CATALOG**|0x1 (二进制 1)|  
|**TABLE_SCHEMA**|0x2 (二进制 10)|  
|**TABLE_NAME**|0x4 (二进制 100)|  
|**TABLE_TYPE**|0x8 （二进制 1000 个）|  
  
 接下来，请注意，没有为每个限制的一位。 因为你想要支持**TABLE_NAME**仅，将返回在 0x4`rgRestrictions`元素。 如果你支持**TABLE_CATALOG**和**TABLE_NAME**，将返回 0x5 (二进制 101)。  
  
 默认情况下，实现返回的 0 （不支持任何限制） 的任何请求。 UpdatePV 是提供程序支持限制的一个示例。  
  
### <a name="example"></a>示例  
 此代码摘自[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)示例。 UpdatePv 支持三个要求的架构行集： `DBSCHEMA_TABLES`， **DBSCHEMA_COLUMNS**，和**DBSCHEMA_PROVIDER_TYPES**。 作为示例，了解如何在你的提供程序中实现架构支持，此主题将指导你完成实现**DBSCHEMA_TABLE**行集。  
  
> [!NOTE]
>  示例代码可能会与不同列出的内容此处;你应将示例代码视为多最新版本。  
  
 添加架构支持的第一步是确定想要支持哪些限制。 若要确定哪些限制可用于架构行集，查看 OLE DB 规范的定义**IDBSchemaRowset**。 以下是主定义，你将看到包含架构行集名称、 限制数目和限制列的表。 选择你想要支持并记下的限制和限制列数的架构行集。 例如，`DBSCHEMA_TABLES`支持四个限制 (**TABLE_CATALOG**， **TABLE_SCHEMA**， **TABLE_NAME**，和**TABLE_TYPE**):  
  
```  
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,   
   ULONG* rgRestrictions)  
{  
    for (ULONG l=0; l<cRestrictions; l++)  
    {  
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
            rgRestrictions[l] = 0x0C;  
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))  
                 rgRestrictions[l] = 0x04;  
             else if (InlineIsEqualGUID(rguidSchema[l],  
                                        DBSCHEMA_PROVIDER_TYPES))  
                      rgRestrictions[l] = 0x00;  
   }  
}  
```  
  
 一个位表示每个限制列。 如果你想要支持限制 （即，可以通过它查询），将该位设置为 1。 如果不希望支持限制，则将该位设置为零。 在上面的代码行，UpdatePV 支持**TABLE_NAME**和**TABLE_TYPE**限制`DBSCHEMA_TABLES`行集。 这些是第三个 （位掩码 100） 和第四个 （位掩码 1000年） 限制。 因此，UpdatePv 的位掩码是 1100年 （或 0x0C）：  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 以下`Execute`函数是正则行集相似。 你有三个自变量： `pcRowsAffected`， `cRestrictions`，和`rgRestrictions`。 `pcRowsAffected`变量是输出参数，提供程序可以在架构行集返回的行的计数。 `cRestrictions`参数是输入的参数包含传递给提供程序使用者的限制数目。 `rgRestrictions`参数是数组的**VARIANT**包含限制值的值。  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 `cRestrictions`变量根据总数的限制的架构行集，而无论提供程序是否支持它们。 因为 UpdatePv 支持两个限制 （第三和第四个），此代码仅查找`cRestrictions`值大于或等于 3。  
  
 值**TABLE_NAME**限制存储在`rgRestrictions[2]`（同样，从零开始的数组中的第三个限制为 2）。 你需要检查的限制不是`VT_EMPTY`以实际支持它。 请注意， **VT_NULL**是否不等于`VT_EMPTY`。 **VT_NULL**指定一个有效限制值。  
  
 表名的 UpdatePv 定义是到文本文件的完全限定的路径名称。 提取的限制值，然后尝试打开该文件以确保该文件确实实际存在。 如果文件不存在，则返回`S_OK`。 这看起来可能有点缓慢但哪些代码真正通知使用者是由指定的名称没有任何支持的表。 `S_OK`返回表示代码是否正确执行。  
  
```  
USES_CONVERSION;  
enum {  
            sizeOfszFile = 255  
};  
CTABLESRow  trData;  
FILE        *pFile = NULL;  
TCHAR       szFile[ sizeOfszFile ];  
errcode     err = 0;  
  
// Handle any restrictions sent to us. This only handles  
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th   
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets   
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04   
// for a total of (0x0C)  
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)  
{  
    CComBSTR bstrName = rgRestrictions[2].bstrVal;  
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))  
    {  
        // Check to see if the file exists  
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));  
        if (szFile[0] == _T('\0') ||   
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))  
        {  
            return S_OK;// Their restriction was invalid return no data  
        }  
        else  
        {  
            fclose(pFile);  
        }  
    }  
}  
```  
  
 支持的第四个限制 (**TABLE_TYPE**) 类似于第三个限制。 检查值是否不`VT_EMPTY`。 此限制仅返回表类型，**表**。 若要确定的有效值`DBSCHEMA_TABLES`，查看的附录 B *OLE DB 程序员参考*中**表**行集部分。  
  
```  
// TABLE_TYPE restriction:  
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)  
{  
    CComBSTR bstrType = rgRestrictions[3].bstrVal;  
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))  
    {  
        // This is kind of a blind restriction.  
        // This only actually supports  
        // TABLES so if you get anything else,   
        // just return an empty rowset.  
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)  
            return S_OK;  
    }  
}  
```  
  
 这是实际创建的行集的行条目。 变量`trData`对应于**CTABLESRow**，OLE DB 提供程序模板中定义的结构。 **CTABLESRow**对应于**表**附录 B 中的 OLE DB 规范的行集定义。 你只有一个要添加，因为一次只能支持一个表的行。  
  
```  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 只有三个列都设置 UpdatePV: **TABLE_NAME**， **TABLE_TYPE**，和**说明**。 你应记下为其返回的信息的列，因为在实现时，你需要此信息`GetDBStatus`:  
  
```  
    _ATLTRY  
    {  
        m_rgRowData.Add(trData);  
    }  
    _ATLCATCHALL()  
    {  
        return E_OUTOFMEMORY;  
    }  
    //if (!m_rgRowData.Add(trData))  
    //    return E_OUTOFMEMORY;  
    *pcRowsAffected = 1;  
    return S_OK;  
}  
```  
  
 `GetDBStatus`函数对于的架构行集的正确操作十分重要。 因为不返回数据中每个列**表**行集，你需要指定哪些列你返回的数据，并不希望这样做。  
  
```  
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)  
{  
    ATLASSERT(pColInfo != NULL);  
  
    switch(pColInfo->iOrdinal)  
    {  
    case 3:     // TABLE_NAME  
    case 4:     // TABLE_TYPE  
    case 6:     // DESCRIPTION  
        return DBSTATUS_S_OK;  
        break;  
    default:  
        return DBSTATUS_S_ISNULL;  
    break;  
    }  
}  
```  
  
 因为你`Execute`函数返回数据**TABLE_NAME**， **TABLE_TYPE**，和**说明**字段从**表**行集，你可以在附录 B 的 OLE DB 规范中查找和确定 （通过倒计时从顶部），它们是序号 3、 4 和 6。 对于每个这些列，返回**DBSTATUS_S_OK**。 对于所有其他列，返回**是 DBSTATUS_S_ISNULL**。 务必返回此状态，因为使用者可能无法理解，则返回值是**NULL**还是其他内容。 同样，请注意， **NULL**不等同于为空。  
  
 有关 OLE DB 架构行集接口的详细信息，请参阅[IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) OLE DB 程序员参考中的接口。  
  
 有关如何使用使用者信息**IDBSchemaRowset**方法，请参阅[用架构行集合获取元数据](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)。  
  
 有关支持架构行集的提供程序的示例，请参阅[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)示例。  
  
## <a name="see-also"></a>请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)