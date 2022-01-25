# MkDocs 安裝

詳細的指南

---

## 需求

MkDocs 需要最新版本的 [Python] 和 Python 包管理器 [pip]，才能安裝在您的系統上。

您可以檢查是否已經從命令行安裝了這些：

```bash
$ python --version
Python 3.8.2
$ pip --version
pip 20.0.2 from /usr/local/lib/python3.8/site-packages/pip (python 3.8)
```

如果你已經安裝了這些套件，你可以跳到 [安裝 MkDocs](#installing-mkdocs)。

### 安裝 Python

使用您選擇的套件管理器安裝 [Python]，或者從 [python.org] 下載適合您系統的安裝程序並運行它。

!!! 注意
    如果您在 Windows 上安裝 Python，如果安裝程序提供了這樣的選項（默認情況下通常是關閉的），請務必勾選`將 Python 添加到您的 PATH 中`。

    ![Add Python to PATH](../img/win-py-install.png)

### 安裝 pip

如果您使用的是最新版本的 Python，則很可能會默認安裝 Python 套件管理器 [pip] 。然而，您可能需要將 pip 升級到最新版本：

```bash
pip install --upgrade pip
```

如果您第一次安裝 pip，請下載 [get-pip.py]。然後運行以下命令進行安裝：

```bash
python get-pip.py
```

## 安裝 MkDocs

使用 pip 安裝 `mkdocs`：

```bash
pip install mkdocs
```

您現在應該在系統上安裝了 `mkdocs` 命令。運行 `mkdocs --version` 以檢查一切是否正常。

```bash
$ mkdocs --version
mkdocs, version 1.2.0 from /usr/local/lib/python3.8/site-packages/mkdocs (Python 3.8)
```

!!! 注意
    如果您想為 MkDocs 安裝 man 幫助頁，[click-man] 工具可以為您生成和安裝它們。只需運行以下兩個命令：

        pip install click-man  
        click-man --target path/to/man/pages mkdocs

    請參閱 [click-man 文件]，了解為什麼 pip 不會自動生成和安裝 man 幫助頁。

!!! 注意
    如果您使用的是 Windows，則上述某些命令可能無法直接使用。

    一個快速的解決方案可能是在每個 Python 命令前加上 `python -m` 這樣的前綴：

        python -m pip install mkdocs  
        python -m mkdocs

    要獲得更持久的解決方案，您可能需要編輯 `PATH` 環境變量以包含 `Scripts` 的 Python 安裝目錄。最新版本的 Python 包含一個為您執行此操作的腳本。導覽到您的 Python 安裝目錄（例如 `C:\Python38\`），打開 `Tools`，然後 `Scripts` 文件夾，雙擊運行 `win_add2path.py`。或者，您可以下載 [script][a2p] 並運行它 (`python win_add2path.py`)。

[Python]: https://www.python.org/
[python.org]: https://www.python.org/downloads/
[pip]: https://pip.readthedocs.io/en/stable/installing/
[get-pip.py]: https://bootstrap.pypa.io/get-pip.py
[click-man]: https://github.com/click-contrib/click-man
[click-man 文件]: https://github.com/click-contrib/click-man#automatic-man-page-installation-with-setuptools-and-pip
[a2p]: https://github.com/python/cpython/blob/master/Tools/scripts/win_add2path.py
