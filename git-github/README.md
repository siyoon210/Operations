# Git & Github

## (20.07.14) github remote branch 이름변경
- git local branch 이름변경
    ```
    git branch -m old_branch new_branch         # Rename branch locally    
    ```

- git remote branch 삭제!
    ```
    git push origin :old_branch                 # Delete the old branch    
    ```

- git remote에 바뀐 이름으로 다시 push
    ```
    git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote
    ```

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
