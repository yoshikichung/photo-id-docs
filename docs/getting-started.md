# MkDocs 入門

入門教程

---

## 安裝

要安裝 MkDocs，請從命令行運行以下命令：

```bash
pip install mkdocs
```

有關詳細信息，請參閱 [安裝指南]。

## 創建一個新專案

入門非常簡單。要創建新專案，請從命令行運行以下命令：

```bash
mkdocs new my-project
cd my-project
```

花點時間查看為您創建的初始專案。

![The initial MkDocs layout](img/initial-layout.png)

有一個名為 `mkdocs.yml` 的配置文件和一個名為 `docs` 的文件夾，其中將包含您的文件源檔（`docs` 是 [docs_dir] 配置設定的默認值）。現在該 `docs` 文件夾只包含一個文件頁面，名為 `index.md`。

MkDocs 帶有一個內置的開發伺服器，可讓您在處理文件時預覽文件。確保您與 `mkdocs.yml` 配置文件位於同一目錄中，然後通過運行 `mkdocs serve` 命令啟動伺服器：

```bash
$ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
[I 160402 15:50:43 server:271] Serving on http://127.0.0.1:8000
[I 160402 15:50:43 handlers:58] Start watching changes
[I 160402 15:50:43 handlers:60] Start detecting changes
```

在瀏覽器中打開 `http://127.0.0.1:8000/` ，您將看到正在顯示的預設主頁：

![The MkDocs live server](img/screenshot.png)

開發伺服器還支持自動重新加載，並且只要配置文件、文件目錄或主題目錄中的任何內容發生更改，就會重新構建您的文件。

在您選擇的文字編輯器中打開 `docs/index.md` 文件，將初始標題更改為 `MkLorum`，然後保存更改。您的瀏覽器將自動重新加載，您應該會立即看到更新的文件。

現在嘗試編輯配置文件 `mkdocs.yml`，更改 [`site_name`][site_name] 設置 `MkLorum` 並保存文件。

```yaml
site_name: MkLorum
site_url: https://example.com/
```

您的瀏覽器會立即重新加載，您會看到新站點名稱生效。

![The site_name setting](img/site-name.png)

**注意**  
> [`site_name`][site_name] 和 [`site_url`][site_url] 配置選項是配置文件中僅有的兩個必需選項。當您創建一個新專案時，該 `site_url`  選項被分配置換字串值 `https://example.com`。如果最終位置已知，您現在可以更改設置以指向它，或者您可以選擇暫時不理會它。只需確保在站點部署到生產伺服器之前對其進行編輯。

## 添加頁面

現在在您的文件中添加第二頁：

```bash
curl 'https://jaspervdj.be/lorem-markdownum/markdown.txt' > docs/about.md
```

由於我們的文件站點將包含一些導覽標題，您可能需要編輯配置文件並通過添加 [`nav`][nav] 設置在導航標題中添加有關每個頁面的順序、標題和嵌套的一些信息：

```yaml
site_name: MkLorum
site_url: https://example.com/
nav:
    - Home: index.md
    - About: about.md
```

保存您的更改，您現在將看到一個導航欄， 左側有 `Home` 和 `About` 項目，右側有 `Search`、`Previous` 和 `Next` 項目。

![Screenshot](img/multipage.png)

嘗試選單項並在頁面之間來回導覽，然後點擊 `Search`。將出現一個搜索對話框，允許您搜索任何頁面上的任何文字。請注意，搜索結果包括網站上每次出現的搜索詞，並直接連接到出現搜索詞的頁面部分。您無需任何配置即可獲得所有這些。

![Screenshot](img/search.png)

## 主題化我們的文件

現在更改配置文件以通過更改主題來更改文件的顯示方式。編輯 `mkdocs.yml` 文件並添加 [`theme`][theme] 設置：

```yaml
site_name: MkLorum
site_url: https://example.com/
nav:
    - Home: index.md
    - About: about.md
theme: readthedocs
```

保存您的更改，您將看到正在使用的 ReadTheDocs 主題。

![Screenshot](img/readthedocs.png)

## 更改 Favicon 圖示

默認情況下，MkDocs 使用 [MkDocs favicon] 圖示。要使用不同的圖示，請在 `docs` 目錄中創建一個子目錄 `img`，並將您的自訂 `favicon.ico` 檔案複製到該目錄。MkDocs 將自動檢測並使用該文件作為您的 favicon 圖示。

[MkDocs favicon]: img/favicon.ico

## 建構網站

這看起來不錯，您已準備好部署 `MkLorum` 文件。首先建構文件：

```bash
mkdocs build
```

這將創建一個名為 `site` 新目錄，查看目錄內部：

```bash
$ ls site
about  fonts  index.html  license  search.html
css    img    js          mkdocs   sitemap.xml
```

請注意您的源文件已輸出為兩個名為 `index.html` 和 `about/index.html` 的 HTML 檔案。您還可以將各種其他媒體作為文件主題的一部分複製到 `site` 目錄中。你甚至有一個 `sitemap.xml` 和 `mkdocs/search_index.json`。

如果您正在使用例如 `git` 源碼控制，您可能不想檢查您的文件建構到存儲庫中。添加一行包含 `site/` 到您的 `.gitignore` 檔案中。

```bash
echo "site/" >> .gitignore
```

如果您正在使用另一個源碼控制工具，您需要查看其文件以了解如何忽略特定目錄。

## 其他命令和選項

還有各種其他可用的命令和選項。有關命令的完整列表，請使用以下 `--help` 選項：

```bash
mkdocs --help
```

要查看給定命令的可用選項列表，請使用該命令 `--help` 選項。例如，要獲取該 `build` 命令可用的所有選項的列表，請運行以下命令：

```bash
mkdocs build --help
```

## 部署

您剛剛建構的文件站點僅使用靜態文件，因此您幾乎可以從任何地方託管它。只需將整個 `site` 目錄的內容上傳到您託管網站的任何位置，這樣就完成了。有關許多常見主機的具體說明，請參閱 [部署您的文件][deploy] 頁面。

## 獲得幫助

有關 MkDocs 的所有功能的完整文件，請參閱 [用戶指南]。

要獲得有關 MkDocs 的幫助，請使用 [GitHub 討論] 或 [GitHub 問題]。


[安裝指南]: user-guide/installation.md
[docs_dir]: user-guide/configuration.md#docs_dir
[deploy]: user-guide/deploying-your-docs.md
[nav]: user-guide/configuration.md#nav
[GitHub 討論]: https://github.com/mkdocs/mkdocs/discussions
[GitHub 問題]: https://github.com/mkdocs/mkdocs/issues
[site_name]: user-guide/configuration.md#site_name
[site_url]: user-guide/configuration.md#site_url
[theme]: user-guide/configuration.md#theme
[用戶指南]: user-guide/index.md
