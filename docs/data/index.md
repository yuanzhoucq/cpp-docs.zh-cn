---
layout: LandingPage
title: "Visual C++ 中的数据访问"
translationtype: Human Translation
ms.sourcegitcommit: d4b97ed874b145f9c6d9a9536476243bba0fd1c1
ms.openlocfilehash: bcec6bba72b48c8fc766c2d74dc31d8e47a239f9
ms.lasthandoff: 03/06/2017

---
# <a name="data-access-in-visual-c"></a>Visual C++ 中的数据访问

几乎所有数据库产品（SQL 和 NoSQL）都提供用于本机 C++ 应用程序的接口。 行业标准接口是 ODBC，所有主要 SQL 数据库产品和多数 NoSQL 产品都支持该接口。 对于非 Microsoft 产品，请咨询供应商，了解详细信息。 此外，还提供具有各种许可条款的第三方库。

自 2011 年起，Microsoft 已将 ODBC 作为本机应用程序连接到本地和云中 Microsoft SQL Server 数据库的标准接口。 有关详细信息，请参阅[数据访问编程\( MFC ATL\)](data-access-programming-mfc-atl.md)。 C++/CLI 库可以使用本机 ODBC 驱动程序或 ADO.NET。 有关详细信息，请参阅[使用 ADO.NET 进行数据访问 (C++/CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) 和[在 Visual Studio 中访问数据](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)。

<ul class="panelContent cardsF">
<li>
        <a href="/azure/sql-database/sql-database-develop-cplusplus-simple">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/azure/media/index/SQLDatabase.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>使用 C 和 C++连接到 SQL 数据库</h3>
                        <p>从 C 或 C++ 应用程序连接到 Azure SQL 数据库</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://github.com/Azure/azure-storage-cpp">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/azure/media/index/Storage.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>用于 C++ 的 Microsoft Azure 存储客户端库</h3>
                        <p>[Azure 存储](/azure/storage/storage-introduction)是一种云存储解决方案，用于依赖于持久性、可用性和可扩展性来满足其客户需求的现代应用程序。 使用适用于 C++ 的 Azure 存储客户端库，从 C++ 连接到 Azure 存储。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_drivers.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>适用于 SQL Server 的 ODBC 驱动程序 13.1 – Windows 版本</h3>
                        <p>最新的 ODBC 驱动程序为基于 C/C++ 的应用程序提供对 Microsoft SQL Server 2016 Microsoft Azure SQL 数据库的可靠数据访问。 提供对各种功能的支持（包括始终加密、Azure Active Directory 以及 AlwaysOn 可用性组）。 此外，还可用于 MacOS 和 Linux。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://msdn.microsoft.com/library/ms130892.aspx">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_api.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>SQL Server Native Client</h3>
                        <p>SQL Server Native Client 是可同时用于 OLE DB 和 ODBC 的独立数据访问应用程序编程接口 (API)，支持 SQL Server 2005 到 SQL Server 2014 的各个版本。 新的应用程序应使用适用于 SQL Server 的 ODBC 驱动程序 13.1。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/cpp/data/data-access-programming-mfc-atl">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_api.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>数据访问编程</h3>
                        <p>介绍使用 Visual C++ 的旧版数据访问编程，其首选方法就是使用其中一个类库，例如活动模板库 (ATL) 或 Microsoft 基础类 (MFC) 库，这样可以简化数据库 API 的处理。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/cpp/data/odbc/open-database-connectivity-odbc">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_multi-connect.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>开放式数据库连接 (ODBC)</h3>
                        <p>Microsoft 基础类 (MFC) 库提供使用开放式数据库连接 (ODBC) 进行编程时所需的类。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/cpp/data/oledb/ole-db-programming">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_generic-database.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>OLE DB 编程</h3>
                        <p>提供讨论 OLE DB 数据库技术和 OLE DB 模板库的概念性主题的链接。 （除非在涉及链接服务器的情况下，否则不建议将 OLE DB 用于新应用程序。）</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    
</ul>

---

<h2>参考</h2>

<ul class="panelContent cardsW">
 <li>
        <a href="https://azure.microsoft.com/develop/cpp/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>Microsoft Azure C 和 C++ 开发人员中心</h3>
                        <p>通过 Azure，用户可以使用喜欢的工具轻松生成更具灵活性、可扩展性和可靠性的 C++ 应用程序。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>如何从 C++ 使用 Blob 存储</h3>
                        <p>Azure Blob 存储是将非结构化数据作为对象/blob 存储在云中的服务。 Blob 存储可以存储任何类型的文本或二进制数据（如文档、媒体文件或应用程序安装程序）。 Blob 存储也称为对象存储。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>ODBC 程序员参考</h3>
                        <p>ODBC 接口用于与 C 编程语言一起使用。 ODBC 接口的使用涉及三大块：SQL 语句、ODBC 函数调用，以及 C 编程。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3><a href="https://www.microsoft.com/download/details.aspx?id=53339" title="Microsoft® ODBC Driver 13.1 for SQL Server® - Windows Download Page">用于 SQL Server 的 ODBC 驱动程序 13.1 </a></h3>
                    </div>
                </div>
            </div>
        </div>        
    </li>
    
</ul>
