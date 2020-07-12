# Git & Github

## (20.07.12) github remote(원격저장소) 관련 명령어
- github remote(원격저장소) 추가하기
    ```
    $ git remote add repo-name https://github.com/...(repo주소)...
    ```

- github remote(원격저장소) branch 업데이트히기
    ```
    $ git remote update
    ```

- github remote(원격저장소) branch 목록 확인하기
    ```
    $ git branch -r
    ```

- github remote(원격저장소) branch 가져오기
   ```
   $ git checkout -t repo-name/branch-name
   ex) git checkout -t origin/feature/create-user
   ```
