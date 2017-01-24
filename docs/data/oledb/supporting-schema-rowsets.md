---
title: "支持架构行集合 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 使用者模板, 架构行集合"
  - "OLE DB 提供程序, 架构行集合"
  - "OLE DB, 架构行集合"
  - "架构行集合"
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 支持架构行集合
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

架构行集合允许使用者获得有关数据存储区的信息，而不必知道它的基础结构或架构。  例如，数据存储区可以使表组织成用户定义的层次结构，因此除了通过读取，没有其他方法可以确保得到架构的知识。（作为另一个示例，注意 Visual C\+\+ 向导使用架构行集合生成使用者的访问器。）为了使使用者可以这样做，提供程序的会话对象公开 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 接口上的方法。  在 Visual C\+\+ 应用程序中，使用 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 类实现 **IDBSchemaRowset**。  
  
 `IDBSchemaRowsetImpl` 支持以下方法：  
  
-   [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) 检查架构行集合限制的有效性。  
  
-   [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) 为模板参数指定的对象实现 COM 对象 creator 函数。  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 指定在特定架构行集合上支持哪些限制。  
  
-   [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) 返回架构行集合（从接口继承）。  
  
-   [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) 返回可由 `IDBSchemaRowsetImpl::GetRowset`（从接口继承）访问的架构行集合列表。  
  
## “ATL OLE DB 提供程序向导”支持  
 “ATL OLE DB 提供程序向导”在会话头文件中创建三个架构类：  
  
-   **C** *ShortName* **SessionTRSchemaRowset**  
  
-   **C** *ShortName* **SessionColSchemaRowset**  
  
-   **C** *ShortName* **SessionPTSchemaRowset**  
  
 这些类响应使用者对架构信息的请求；注意 OLE DB 规范要求支持这三个架构行集合：  
  
-   **C** *ShortName* **SessionTRSchemaRowset** 处理表信息（`DBSCHEMA_TABLES` 架构行集合）请求。  
  
-   **C** *ShortName* **SessionColSchemaRowset** 处理列信息（**DBSCHEMA\_COLUMNS** 架构行集合）请求。  向导为这些类提供了示例实现，这些实现为 DOS 提供程序返回架构信息。  
  
-   **C** *ShortName* **SessionPTSchemaRowset** 处理有关提供程序类型的架构信息（**DBSCHEMA\_PROVIDER\_TYPES** 架构行集合）请求。  向导提供的默认实现返回 `S_OK`。  
  
 可以自定义这些类以处理适合提供程序的架构信息：  
  
-   在 **C***ShortName***SessionTRSchemaRowset** 中，必须填写目录、表和说明字段（**trData.m\_szType**、**trData.m\_szTable** 和 **trData.m\_szDesc**）。  向导生成的示例仅使用一行（表）。  其他提供程序可以返回多个表。  
  
-   在 **C***ShortName***SessionColSchemaRowset** 中，将表的名称作为 **DBID** 传递。  
  
## 设置限制  
 架构行集合支持中的一个重要概念是设置限制，通过使用 `SetRestrictions` 来完成。  限制允许使用者只获取匹配行（例如，查找表“MyTable”中的所有列）。  限制是可选的，如果不支持任何限制（默认），则总是返回所有数据。  有关确实支持限制的提供程序示例，请参见 [UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f) 示例。  
  
## 设置架构映射  
 设置像 UpdatePV 的 Session.h 中的这个架构映射：  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 若要支持 **IDBSchemaRowset**，则必须支持 `DBSCHEMA_TABLES`、**DBSCHEMA\_COLUMNS** 和 **DBSCHEMA\_PROVIDER\_TYPES**。  可以酌情添加附加的架构行集合。  
  
 用 `Execute` 方法声明架构行集合类，如 UpdatePV 中的 `CUpdateSessionTRSchemaRowset`：  
  
```  
class CUpdateSessionTRSchemaRowset :   
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,   
                              CTABLESRow, CUpdateSession >  
...  
// Execute looks like this; what pointers does the consumer use?  
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,   
                    ULONG cRestrictions, const VARIANT* rgRestrictions)  
```  
  
 注意 `CUpdateSession` 从 `IDBSchemaRowsetImpl` 继承，所以它具有全部限制处理方法。  使用 `CSchemaRowsetImpl`，声明三个子类（在上面的架构映射中列出）：`CUpdateSessionTRSchemaRowset`、`CUpdateSessionColSchemaRowset` 和 `CUpdateSessionPTSchemaRowset`。  这些子类中的每一个都具有处理各自的一组限制（搜索判据）的 `Execute` 方法。  每个 `Execute` 方法比较 `cRestrictions` 和 `rgRestrictions` 参数的值。  请参见 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 中这些参数的说明。  
  
 有关哪些限制与特定架构行集合相对应的更多信息，请参考架构行集合 GUID 表，该表在 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 的 *OLE DB 程序员参考*中的 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 中。  
  
 例如，如果支持 `DBSCHEMA_TABLES` 上的 **TABLE\_NAME** 限制，则执行以下操作：  
  
 首先，查看 `DBSCHEMA_TABLES`，可看到它支持四个限制（按顺序）。  
  
|架构行集合限制|限制值|  
|-------------|---------|  
|**TABLE\_CATALOG**|0x1（二进制 1）|  
|**TABLE\_SCHEMA**|0x2（二进制 10）|  
|**TABLE\_NAME**|0x4（二进制 100）|  
|**TABLE\_TYPE**|0x8（二进制 1000）|  
  
 下一步，注意每个限制各有一位。  因为希望只支持 **TABLE\_NAME**，所以在 `rgRestrictions` 元素中返回 0x4。  如果支持 **TABLE\_CATALOG** 和 **TABLE\_NAME**，将返回 0x5（二进制 101）。  
  
 默认情况下，实现对任何请求都返回 0（不支持任何限制）。  UpdatePV 是确实支持限制的提供程序示例。  
  
### 示例  
 此代码取自 [UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f) 示例。  UpdatePv 支持三个必需的架构行集合：`DBSCHEMA_TABLES`、**DBSCHEMA\_COLUMNS** 和 **DBSCHEMA\_PROVIDER\_TYPES**。  作为如何在提供程序中实现架构支持的示例，本主题将带领您一步步实现 **DBSCHEMA\_TABLE** 行集合。  
  
> [!NOTE]
>  代码示例可能与此处列出的不同；此代码示例应视为较新版本。  
  
 添加架构支持的第一步是确定打算支持哪些限制。  若要确定哪些限制可用于架构行集合，请查看 OLE DB 规范中的 **IDBSchemaRowset** 定义。  按照主定义，可看到一个表，其中包含架构行集合名称、限制的数目和限制列。  选择要支持的架构行集合，并记下限制的数目和限制列。  例如，`DBSCHEMA_TABLES` 支持四个限制（**TABLE\_CATALOG**、**TABLE\_SCHEMA**、**TABLE\_NAME** 和 **TABLE\_TYPE**）：  
  
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
  
 位表示每个限制列。  如果希望支持限制（即可以通过它查询），将此位设置为 1。  如果不希望支持限制，将此位设置为零。  从以上代码行，UpdatePV 在 `DBSCHEMA_TABLES` 行集合上支持 **TABLE\_NAME** 和 **TABLE\_TYPE** 限制。  这些是第三个（位掩码 100）和第四个（位掩码 1000）限制。  因此，UpdatePv 的位掩码是 1100（或 0x0C）：  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 以下 `Execute` 函数类似于常规行集合中的同名函数。  有三个参数：`pcRowsAffected`、`cRestrictions` 和 `rgRestrictions`。  `pcRowsAffected` 变量是提供程序可以在架构行集合中返回行计数的输出参数。  `cRestrictions` 参数是包含使用者传递给提供程序的限制数的输入参数。  `rgRestrictions` 参数是包含限制值的 **VARIANT** 值数组。  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 `cRestrictions` 变量基于架构行集合的总限制数，与提供程序是否支持它们无关。  UpdatePv 支持两个限制（第三个和第四个），所以此代码只查找一个大于或等于 3 的 `cRestrictions` 值。  
  
 **TABLE\_NAME** 限制的值存储在 `rgRestrictions[2]` 中（从零开始的数组中的第三个限制同样是 2）。  需要检查限制不是 `VT_EMPTY` 以实际支持它。  注意 **VT\_NULL** 不等于 `VT_EMPTY`。  **VT\_NULL** 指定有效的限制值。  
  
 表名的 UpdatePv 定义是文本文件的完全限定路径名。  解压缩限制值然后尝试打开文件以确保文件确实存在。  如果文件不存在，返回 `S_OK`。  这看起来可能有点缓慢，但代码真正通知使用者的是没有受指定名称支持的表。  返回 `S_OK` 表示代码被正确执行。  
  
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
  
 支持第四个限制 \(**TABLE\_TYPE**\) 类似于第三个限制。  检查值不是 `VT_EMPTY`。  该限制只返回表类型 **TABLE**。  若要确定 `DBSCHEMA_TABLES` 的有效值，请在 **TABLES** 行集合节中的《OLE DB 程序员参考》的附录 B 中查找。  
  
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
  
 这是实际为行集合创建行项的地方。  变量 `trData` 与 OLE DB 提供程序模板中定义的结构 **CTABLESRow** 相对应。  **CTABLESRow** 与 OLE DB 规范附录 B 中的 **TABLES** 行集合定义相对应。  因为一次只支持一个表，所以只需添加一行。  
  
```  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  
wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  
wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 UpdatePV 只设置三列：**TABLE\_NAME**、**TABLE\_TYPE** 和 **DESCRIPTION**。  应记下为之返回信息的列，因为在实现 `GetDBStatus` 时需要此信息：  
  
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
  
 `GetDBStatus` 函数对于架构行集合的正确操作非常重要。  由于不为 **TABLES** 行集合中的每个列都返回数据，因此需要指定为哪些列返回数据，不为哪些列返回数据。  
  
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
  
 因为 `Execute` 函数为 **TABLES** 行集合中的 **TABLE\_NAME**、**TABLE\_TYPE** 和 **DESCRIPTION** 字段返回数据，可以在 OLE DB 规范附录 B 中查找并确定（通过从上到下计数）它们是序号 3、4 和 6。  对于那些列中的每一个列，都返回 **DBSTATUS\_S\_OK**。  对于所有其他列，返回 **DBSTATUS\_S\_ISNULL**。  返回此状态很重要，因为使用者可能不理解返回的值为 **NULL** 还是其他什么值。  同样注意 **NULL** 不等效于空。  
  
 有关 OLE DB 架构行集合接口的更多信息，请参见“OLE DB Programmer's Reference”（OLE DB 程序员参考）中的 [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) 接口。  
  
 有关使用者如何才能使用 **IDBSchemaRowset** 方法的信息，请参见[用架构行集合获取元数据](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)。  
  
 有关支持架构行集合的提供程序示例，请参见 [UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f) 示例。  
  
## 请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)