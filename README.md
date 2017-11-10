
# Git Notes

## Repository and Working Directory

<a name="repository"></a>
Repository

 - A repository contains all the files for your project.

 - You may noticed that there is a _.git_ directory in the repository. Let's call it the git directory. In the git directory there are files and folders that compose our repository. Thanks to this, we can track the file status, configure the repository, and so on.

 - To be able to collaborate on any Git project, you need to know how to manage your remote repositories. Remote repositories are versions of your project that are hosted on the Internet or network somewhere.


**[⬆ back to top](#table-of-contents)**

<br />
<br />

Working Directory

 - A folder that contains an initialized Git repository is a working directory.


**[⬆ back to top](#table-of-contents)**

<br />
<br />

## File Status Lifecycle

![File Status Lifecycle](./assets/images/file-status-lifecycle.jpg)

 - When you create or copy a new file in the working directory, the first state of the file is **untracked**.

 - If you want to include the file in your repository, you have to add it using the _add_ command. Once it is added, the state of the file becomes **unmodified**.

 - If you modify a file that is already added to the staging area, it changes its status to **modified**.

 - The staging area is a virtual place that collects all the files you want to include in the next commit. All the files (new or modified) you want to include in the next commit have to be **staged** using the _git add_ command.


 **[⬆ back to top](#table-of-contents)**

 <br />
 <br />

## Git Configuration

<a name="configuration-architecture"></a>
Configuration Architecture

 - The configuration options are stored in plain text files. The _git config_ command is just a convenient tool to edit these files without the hassle of remembering where they are stored and opening them in a text editor.


 **[⬆ back to top](#table-of-contents)**

 <br />
 <br />

<a name="configuration-levels"></a>
Configuration Levels

 - In Git we have three configuration levels which are：
    - System
    - User
    - Repository

 - There are different configuration files for every different configuration level.

 - You can basically set every parameter at every level according to your needs. If you set the same parameters at different levels, the lowest-level parameter hides the top level parameters.

    > System > User > Repository

    - System：every user and its repository will be affected.
      - `git config --system`
      - configuration file path：/usr/local/git/etc/gitconfig (Mac OS)

    - User：every user's repository will be affected.
      - `git config --global`
      - configuration file path：~/.gitconfig (Mac OS)

    - Repository：only the repository in use will be affected.
      - `git config --local`
      - configuration file path：~/<儲存庫所在的資料夾>/.git/config (Mac OS)


**[⬆ back to top](#table-of-contents)**

<br />
<br />

<a name="ignore-some-files-and-folders-by-default"></a>
Ignoring some files and folders by default

 - We can create a _.gitignore_ file in the repository. Git will read it and then skip the  les and folders we listed inside it.

 > For the complete syntax of .gitignore see [Official Git Ignore Document](http://git-scm.com/docs/gitignore).


**[⬆ back to top](#table-of-contents)**

<br />
<br />

## Branch

 - A branch represents an independent line of development for your repository. Think of it as a brand-new working directory, staging area, and project history. Before you create any new branches, you automatically start out with the main branch (called master ).

 > For a visual example, this diagram shows the master branch and the other branch with a bug fix update.

 ![Create New Branch](./assets/images/git-branch-create.jpg)

 - **Origin** is the default upstream repository. Most projects have at least one upstream project which they track. By default _origin_ is used for that purpose.

 - **Master** is the default development branch. Whenever you create a Git repository, a branch named "master" is created, and becomes the active branch.

 > This diagram shows what happens when your local repository has changes that the central repository does not have and you push those changes to it.

 ![Merge Branch](./assets/images/git-branch-merge.jpg)

**[⬆ back to top](#table-of-contents)**

<br />
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
