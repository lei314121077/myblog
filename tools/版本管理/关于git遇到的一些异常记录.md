# ISSUES

## 签名失败，权限被拒绝，无法提交代码到远程仓库  
   
   ```
      sign_and_send_pubkey: signing failed: agent refused operation Permission denied (publickey). 
      fatal: Could not read from remote repository.
      Please make sure you have the correct access rights and the repository exists.
   ```

   * 姿势 一

      ```
      git init 
      git remote remove origin 
      git remote add origin 'your git https url' 
      git push -u origin master
      ```

   * 姿势二

      排查你的ＳＳＨＫＥＹ是否存在远程仓库内

      ```shell
      cat ~/.ssh/id_rsa.pub         
      //复制pub里面的密钥到你的gitlab或者github的settings里面的ＳＳＨＫey里面
      //　然后在尝试git pull origin master或者其它操作      
      ```

      
