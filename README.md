
## [uv](https://docs.astral.sh/uv/)

### install uv
* On Windows
    ```
    powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
    ```
* On MacOS
    ```
    brew install uv
    ```
* On Linux
    ```
    curl -LsSf https://astral.sh/uv/install.sh | sh
    ```

### uv 使用方法

* 用uv 安裝python 環境

    觀看能下載的python 版本
    ```
    uv python list
    ```

    安裝python 3.13
    ```
    uv python install 3.13
    ```

* 專案初始化
    ```
    uv init -p 3.13
    ```

    會預設產生.gitignore, .python-version, pyproject.toml,README.md, 以及自動建立.git

* 執行程式
    此為使用上方初始化的python 版本執行main.py，首次執行會建立.venv 的虛擬環境和uv.lock 
    ```
    uv run .\main.py
    ```

* 虛擬環境新增套件
    ```
    uv pip install XXX
    ```

* 新增pyproject.toml, uv.lock和虛擬環境套件
    ```
    uv add XXX
    ```

* 移除pyproject.toml, uv.lock和虛擬環境套件
    ```
    uv remove XXX
    ```

* 鎖定匯出虛擬環境library
    匯出 uv.lock 更新
    ```
    uv lock
    ```

* 同步更新虛擬環境library
    根據 uv.lock 更新
    ```
    uv sync
    ```

* 套件 樹狀圖
    ```
    uv tree
    ```

* 更新套件
    更新套件會依照 pyproject.toml 檔內的限制，安裝符合條件的版本
    ```
    uv lock --upgrade-package XXX

    uv lock --upgrade
    ```

* 手動檢查相容性
    ```
    uv pip check
    ```

### 管理只有單一程式碼檔的專案

* 新增XXX套件至main.py 
    ```
    uv add --script main.py XXX
    ```

* 移除XXX套件至main.py
    ```
    uv remove --script main.py XXX
    ```

### install ruff (Code lint)

* installed with uv (recommended)

    1. Install Ruff globally.
    ```
    uv tool install ruff@latest
    ```

    2. Or add Ruff to your project.
    ```
    uv add ruff
    ```

* 檢查是否符合規則
    檢查 [ruff.toml#tool.ruff.lint](pyproject.toml#tool.ruff.lint)
    ```
    ruff check
    ```

* 修復符合規則
    ```
    ruff check --fix
    ```

* 檢查修復格式
    ```
    ruff format
    ```


### install pre-commit

* installed with pre-commit

    1. Install globally.
    ```
    uv tool install pre-commit
    ```

    2. Or add Ruff to your project.
    ```
    uv add pre-commit
    ```

* 連結 pre-commit hooks (根據 .pre-commit-config.yaml) 
    ```
    pre-commit install
    ```