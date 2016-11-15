
# Git Notes

### 1. Git Config

git config 設定檔的效果範圍，分為三種層級：系統、使用者、儲存庫 *(預設)*

如果不同層級都設定相同的參數，較低層級會覆蓋較高層級的層級 `系統 >> 使用者 >> 儲存庫`

 - 系統：涵蓋全系統，會影響所有使用者及他們的儲存庫
   - `git config --system`
   - 設定檔路徑：/usr/local/git/etc/gitconfig (Mac OS)
 - 使用者：會影響該使用者的每個儲存庫
   - `git config --global`
   - 設定檔路徑：~/.gitconfig (Mac OS)
 - 儲存庫：只會影響目前的儲存庫
   - `git config --local`
   - 設定檔路徑：~/<儲存庫所在的資料夾>/.git/config (Mac OS)

<br />

### 2. .gitignore：忽略指定檔案的設定檔

在指定 repo 中放入 .gitignore 檔案，可忽略指定的檔案

完整的 .gitignore 語法可參考 [官方 Git Ignore 文件](http://git-scm.com/docs/gitignore)

<br />

### 3. 關於 origin

origin 是遠端儲存庫的預設名稱，如同 master 是本地儲存庫的預設名稱，一樣

<br />

### 4. 本地目錄上傳至遠端

1. 建立一個空資料夾「MyRepo」，並進入它
  ```bash
  $ mkdir MyRepo
  $ cd MyRepo
  ```

2. 將該資料夾轉換成工作目錄，即「初始化」
 ```bash
  $ git init
  ```

  > 此時「MyRepo」裡面將新增一個「.git」資料夾

3. 新增檔案「FirstFile.txt」
  ```bash
  $ touch FirstFile.txt
  ```

4. 將「FirstFile.txt」加入「集結區」
  ```bash
  $ git add FirstFile.txt
  ```

5. 提交「集結區」內容至本地端 repo
  ```bash
  $ git commit -m 'Add FirstFile.txt'
  ```

6. 設定本地端 repo 與 遠端 repo 的參照
  ```bash
  $ git remote add origin https://github.com/mujan5427/MyRepo.git
  ```

7. 將本地端 branch 內容發佈至遠端 repo
  ```bash
  $ git push -u origin master
  ```

<br />

### 5. 常用指令

1. 貯存：暫存目前 branch 的修改內容
   - 儲存：
   ```bash
   $ git stash
   ```

   - 取出：
   ```bash
   $ git stash apply
   ```
   
2. 查看狀態：查看各檔案目前的狀態
   ```bash
   $ git status
   ```
     
3. 設定 Config 用戶資訊
   - 名稱：
   ```bash
   $ git config user.name 'Justin Ho'
   ```
   
   - E-mail：
   ```bash
   $ git config user.email 'mujan5427@gmail.com'
   ```

4. Config Alias
   - 設定：
   ```bash
   $ git config <config level> alias.cm 'commit -m'
   ```
   
   - 刪除：
   ```bash
   $ git config <config level> --unset alias.cm
   ```
   
5. 查看分支
   ```bash
   $ git branch
   ```
   
6. 建立新分支 *(想從哪個 branch 複製，就先切換到那)*
   ```bash
   $ git branch NewBranch
   ```
   
7. 切換分支
   ```bash
   $ git checkout NewBranch
   ```
   
8. 合併分支 *(目前在 master branch)*
   ```bash
   $ git merge NewBranch
   ```
   
9. 套用下載的異動資料
   ```bash
   $ git pull
   ```
   
10. 檢查檔案的異動內容
   ```bash
   $ git blame
   ```
   
11. 選用提交 (cherry picking)：選擇指定 commit，套用到自己目前的 branch
   ```bash
   $ git checkout 我是需要a1b2c3提交的一支分支
   $ git cherry-pick a1b2c3
   ```

<br />

### Reference Information

Git Essentials (Author：Ferdinando Santacroce)

<br />